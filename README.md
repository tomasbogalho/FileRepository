# FileRepository

This project is an Azure Static Website hosted in Azure Blob Storage that displays a directory of files from an Azure File Share. Users can view the file names directly from the web interface.

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Configuration](#configuration)
- [Deployment](#deployment)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Features

- List files from an Azure File Share
- Responsive design

## Prerequisites

- [Azure Storage Account](https://azure.microsoft.com/en-us/services/storage/)

## Setup

1. Clone the repository:

    ```sh
    git clone https://github.com/tomasbogalho/FileRepository.git
    cd FileRepository
    ```

## Configuration

1. **Azure Storage Account**: Ensure you have an Azure Storage Account and a File Share created.

2. **CORS Configuration**: Configure CORS in your Azure Storage Account to allow requests from your static website's domain.

    - Navigate to your storage account in the Azure portal.
    - Go to `Settings` > `Resource sharing (CORS)`.
    - Add a new CORS rule:
        - Allowed origins: `https://your-static-website.blob.core.windows.net`
        - Allowed methods: `GET, OPTIONS`
        - Allowed headers: `*`
        - Exposed headers: `*`
        - Max age: `3600`

3. **Generate SAS Token**:

    - Navigate to your storage account in the Azure portal.
    - Go to `Shared access signature` under `Settings`.
    - Set the following parameters:
        - **Allowed services**: File
        - **Allowed resource types**: Service, Container, Object
        - **Allowed permissions**: Read, List
        - **Start and expiry date/time**: Set the appropriate start and expiry date/time.
        - **Allowed IP addresses**: (Optional) Specify the IP addresses that can use the SAS.
        - **Allowed protocols**: HTTPS
    - Click on `Generate SAS token and URL`.
    - Copy the SAS token value.

## Deployment

1. **Deploy to Azure Blob Storage**:

    - Navigate to your storage account in the Azure portal.
    - Go to `Static website` under `Settings`.
    - Enable static website hosting.
    - Set the `Index document name` to [index.html](http://_vscodecontentref_/2).
    - Upload your website files (e.g., [index.html](http://_vscodecontentref_/3), `styles.css`, `app.js`) to the `$web` container.

2. **Update [index.html](http://_vscodecontentref_/4)**:

    - Replace `<storage-account-name>`, `<file-share-name>`, and `<SAS-Token>` in the [index.html](http://_vscodecontentref_/5) file with your actual Azure Storage account name, file share name, and SAS token.

## Usage

1. **Access the Website**:

    - Navigate to the URL of your deployed static website to see the file share directory listing.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
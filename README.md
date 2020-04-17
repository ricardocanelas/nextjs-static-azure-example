This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/zeit/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Deploy on Azure Storage

**Azure**

- Create [storage account](https://portal.azure.com/?quickstart=true#create/Microsoft.StorageAccount-ARM), if you don't have yet.
- Create container
  - Go to `<your-storage-account>` / Overview / Container
  - Name of the container: `$web`
  - Public access level: `blog`
- Enable the static website
  - `<your-storage-account> / Setting Static Website /`
  - Enable & Save
  - Index document name: `index.html`
  - Error document path: `404.html`
  - Save again

**Github**

- In your repository `https://github.com/<my-user>/<my-repo>/settings/`secrets
- Add Secret value
  - name: AZURE_STORAGE_CONNECTION_STRING
  - value: <azure-portal/your-storage-account/settings/access-keys/secondary-endpoint>
- Go to `https://github.com/<my-user>/<my-repo>/actions/new`
  - Click on `Set up a workflow yourself` button
  - Include [this content](https://github.com/ricardocanelas/nextjs-static-azure-example/blob/master/.github/workflows/nodejs.yml)
    - Inspirated by: https://github.com/lynshi/personal-website/blob/master/.github/workflows/deploy.yml

**Storage**

Your container will content something like that:

```js
|-- $web
    |-- 404/
        |-- index.html
    |-- _next/
        |-- static/
            |-- chunks/
                |-- framework.js
                |-- a3234chunk1.js
                |-- b6810chunk2.js
                |-- c3452chunk3.js
            |-- runtime/
                |-- main.js
                |-- polyfills.js
                |-- webpack.js
    |-- about/
        |-- index.html
    |-- show/
        |-- 11465/
            |-- index.html
        |-- 22309/
        |-- 33618/
        |-- 756/
        |-- .../
    |-- 404.html
    |-- favico.ico
    |-- index.html
    |-- zeit.svg
```
## Example

```yml
jobs:
  # Call the workflow to build the project
  build:
    uses: opendreamnet/github-config/.github/workflows/build-docker-image.yml@main
    secrets: inherit
    with:
      environment: production
      runs-on: '"ubuntu-high"'
      docker-image-name: ghcr.io/opendreamnet/upscale
      docker-file: ./docker/Dockerfile
      docker-build-args: |
        S3_BUCKET=${{ vars.S3_BUCKET }}
        S3_REGION=${{ vars.S3_REGION }}
        S3_ENDPOINT=${{ vars.S3_ENDPOINT }}
      docker-build-secret-keys: '["S3_ACCESS_KEY_ID", "S3_SECRET_ACCESS_KEY"]'
```
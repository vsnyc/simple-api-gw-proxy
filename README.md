# simple-api-gw-proxy
Sample code to demonstrate Amazon API Gateway proxying to an AWS Lambda function

## Steps to test
1. Sync the repo to a S3 bucket you own
   `aws s3 sync . s3://<my-bucket>/simple-api-gw-proxy/`
   
2. Deploy the proxy template
   ```
    aws cloudformation create-stack --stack-name <stack-name> \
     --template-url "https://s3.amazonaws.com/<my-bucket>/simple-api-gw-proxy/templates/agi-gw-proxy.yaml" \
     --capabilities CAPABILITY_AUTO_EXPAND CAPABILITY_IAM \
     --parameters  ParameterKey=TemplatesBucket,ParameterValue=<my-bucket>
   ```
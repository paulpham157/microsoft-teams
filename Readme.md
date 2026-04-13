# GitHub + Microsoft Teams Integration

To learn how to install and use the GitHub integration in Teams please refer to our [docs](https://docs.github.com/integrations/how-tos/teams)

<details>

<summary>GHEC Integration</summary>

### GHEC with Data Residency (ghe.com)
The data residency version of the Microsoft Teams app can be installed from AppSource [here](https://appsource.microsoft.com/en-us/product/office/WA200008122). 

</details>

<details>

<summary>GHES Integration</summary>

## GHES Integration

We are announcing GA for GHES integration with Microsoft Teams with GHES 3.8. 

With this integration, you will now be able to subscribe to your repositories in your GHES instance and get live updates about your Issues, PRs, Commits and Deployments in your MS teams channels and personal app. And you can also take actions like commenting, open/close issues and approve your deployments directly from chat. 

### How does this integration work?
Starting with GHES 3.8, we are shipping a dedicated ChatOps service bundled along with your GHES server. And you can choose to integrate with Microsoft Teams. With our integration for GHES, you will have
1. A fully secure and scalable experience:
All your subscriptions info and any other metadata stays within your GHES setup. So, you don't have to worry about data flowing to any external service.

2. Connectivity between GHES and Azure Bot:
Our GHES integration is not just a notification service. It will also enable you to perform actions directly from chat. So, the only prerequisite you need is to ensure your GHES instance is accessible from Azure Bot that is deployed when MS Teams integration is set up on GHES. 

### Configuration steps
The existing GitHub app you see in the app store can only be used for GHEC (hosted GitHub) integration. To integrate your GHES instance with MS Teams, you need to configure a private GHES app. Here are the steps to integrate with GHES.

1. Navigate to "your-ghes-url:8443" and go to section “Chat Integrations”
  
  ![image3](https://user-images.githubusercontent.com/9424117/223645857-b115adba-558e-4b2f-9363-d6b5da0c9c59.png)
  
2. Select the checkbox Enable GitHub Chat Integration
3. Select MS teams tab
4. Register application on Azure portal by going to the link mentioned.
5. Enter your application registration name and for account type select “Multi-tenant” and click “Register 
  
  ![image2](https://user-images.githubusercontent.com/9424117/223646172-d57582fa-ee33-4e0c-897f-f79c33838956.png)
  
6. Take note of application ID and tenant ID

  <img width="1227" height="358" alt="image" src="https://github.com/user-attachments/assets/03338bf8-5b90-435e-9373-519e6a51b550" />
  
7. Click on “Certificates & secret” and generate a new client secret.
8. Take note of application ID, tenant ID and client secret and navigate back GHES instance settings
9. Click on Deploy to Azure button
  
  <img width="609" alt="image7" src="https://user-images.githubusercontent.com/9424117/223646342-83542888-e97d-494f-b2b5-89e4098496ff.png">
  
10. Select the subscription and resource group for Azure bot to be deployed. Enter the GHES hostname, the app ID and tenant ID previously generated and click Review + create.

    - If your GitHub Enterprise instance **is reachable on the public internet** make sure that the `Append '_msteams' to path` option is **checked**.
    - If your GitHub Enterprise instance **is not reachable on the public internet and requires a proxy** make sure that the `Append '_msteams' to path` option is **unchecked**. Also, enter the URL that will forward the traffic to the instance in `GHES Instance Host Name`.
  
  <img width="725" height="661" alt="image" src="https://github.com/user-attachments/assets/2ad2896b-5bc4-4bed-bce5-c2e6017fa905" />

11. Once the bot is provisioned. Return to the settings page and enter the app ID, tenant ID and client secret. If the GHES endpoint is not reachable on public internet and the traffic is going to be forwarded enter that URL in `Public Endpoint URL`. Click on Save client settings. 
  
  <img width="979" height="589" alt="image" src="https://github.com/user-attachments/assets/ded71524-92a1-4930-9c8a-c2c871b5a6e1" />
  
12. Once the settings are saved download the manifest from the generate manifest button. Click on green Save settings to persist the settings on the instance. Once settings are applied (could take 5-15 mins depending on the configuration). 
  
  <img width="1130" height="538" alt="image" src="https://github.com/user-attachments/assets/c87b26cb-168c-43cf-88d0-7c7e6bf02329" />

13. Upload the manifest to MS teams app. Steps [here](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/apps-upload#upload-your-app) 

And now you have a dedicated GHES integration with Microsoft teams. All the features that are available in our hosted GitHub integration (GHEC) will be available in GHES integration.

</details>

## Questions? Need help?
If you need support or help please fill out GitHub's [Support form](https://support.github.com/contact?legacy&source=subtitle&tags=rr-general-technical&subject%5D=Re:Microsoft%20Teams%20Integration) and your request will be routed to the right team at GitHub.

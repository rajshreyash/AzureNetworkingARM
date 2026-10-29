Azure Networking ARM Template

This project contains an Azure Resource Manager (ARM) template that defines a basic Azure networking environment with one Virtual Network and one subnet.

Architecture:

The template creates the following resources:

• One Azure Virtual Network
• One subnet within the Virtual Network

Network Configuration

• Virtual Network name: practice-vnet
• Virtual Network address space: 10.0.0.0/16
• Subnet name: application-subnet
• Subnet address prefix: 10.0.1.0/24
• Azure region: Central India

The subnet address prefix is contained within the Virtual Network address space.

Project Structure:

AzureNetworkingARM
├── azuredeploy.json
├── azuredeploy.parameters.json
└── README.md

Files:

azuredeploy.json

Defines the Azure infrastructure resources, parameters, and outputs.

The template uses the following Azure resource type:

Microsoft.Network/virtualNetworks

The subnet is defined within the Virtual Network resource.

azuredeploy.parameters.json

Provides deployment-specific values for:

• Azure region
• Virtual Network name
• Virtual Network address prefix
• Subnet name
• Subnet address prefix

Template Outputs:

After a successful deployment, the template returns:

• Virtual Network name
• Virtual Network resource ID
• Subnet name
• Subnet resource ID

Local Validation

Both JSON files were checked locally using PowerShell:

Get-Content .\azuredeploy.json -Raw |
ConvertFrom-Json |
Out-Null

Get-Content .\azuredeploy.parameters.json -Raw |
ConvertFrom-Json |
Out-Null

The files passed local JSON syntax validation successfully.

Deployment Prerequisites

To deploy this template, the user requires:

An active Azure subscription
An existing Azure resource group
Permission to create networking resources
Azure CLI, Azure PowerShell, Azure Cloud Shell, or access to the Azure portal

Deployment Using Azure CLI

az deployment group create `    --name networking-deployment`
--resource-group <resource-group-name> `    --template-file .\azuredeploy.json`
--parameters .\azuredeploy.parameters.json

Replace <resource-group-name> with the target Azure resource group.

Deployment Using Azure PowerShell

New-AzResourceGroupDeployment `    -Name "networking-deployment"`
-ResourceGroupName "<resource-group-name>" `    -TemplateFile ".\azuredeploy.json"`
-TemplateParameterFile ".\azuredeploy.parameters.json"

Deployment Status
The template was created and locally validated as a practice task. It was not deployed because an active Azure subscription was not available.

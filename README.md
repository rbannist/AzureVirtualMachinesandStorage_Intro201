# Azure Virtual Machines and Storage - Intro - 201

In this lab you will inspect the 'off-the-shelf' VM options available to you in Azure, provision a VM with a single unmanaged disk into a resource group, provision a VM with a Managed Disk into a different resource group, and then use configuration management tooling to build out a simple web server runtime environment.  Lastly, you will briefly inspect a representation of what you have created in the Azure Portal.
<br><br><br>
## Exercise 1 - VM Images and Sizes

Azure Virtual Machines are available in a number of configurations that fit under different VM families.  Here we will inspect what VM sizes are available in different Azure Regions.  We will then view what base OS images are available in different regions' galleries.  One of the images will be used to build bootable OS disks when we provision VMs in later steps.
<br><br>
#### Step 1 - Navigate to the Azure Portal and open the Cloud Shell

URL = `https://portal.azure.com`

Cloud Shell:
![Cloud Shell](images/1_CloudShell.png?raw=true)

<br>
![Cloud Shell](images/2_CloudShell.png?raw=true)

<br>
#### Step 2 - Select your subscription if more than one is available to you

Firstly, list the Subscriptions available to your user:

```
az account list
```

![Subscription List](images/3_AccountList.png?raw=true)

Then select the appropriate subscription:

```
az account set --subscription 'guid'
```

For example, in the image below I am selecting my MSDN ('Visual Studio Enterprise') subscription:

![Set Subscription](images/4_AccountSet.png?raw=true)

<br>
#### Step 3 - Inspect the VM sizes available in the North Europe and UK South Regions using Azure CLI

Enter the following in the Cloud Shell:

```
az vm list-sizes -l northeurope -o table
```

![Set Subscription](images/5_ListVMSizesNorthEurope.png?raw=true)

followed by:

```
az vm show sizes -l uksouth -?
```

![Set Subscription](images/6_ListVMSizesUKSouth.png?raw=true)

Compare the outputs and identify the differences.

At the time of writing, the differences are:

| UK South |
| ------------------------------------------- |
| + G Series (Very high balanced performance) |
| + L Series (Storage Optimised) |
| + M Series (Memory Optimised) |

<br>
#### Step 4 - Inspect the VM sizes available in the North Europe and UK South Regions using PowerShell

Switch the Cloud Shell to PowerShell mode:

![Switch to PowerShell Cloud Shell](images/7_SwitchToPowerShell.png?raw=true)

Enter the following in the Cloud Shell:

```

```

followed by:

```

```

You should see the same differences as when using the CLI.

<br>
#### Step 5 - Inspect the VM images available in all Regions using PowerShell

Enter the following in the Cloud Shell:

```
Get-AzureRmImage | Select * | Out-Gridview -Passthru
```

You should see something like this:

'img'

To view all of the images that you can use, enter this:

```
Get-AzureRmImage | SELECT ImageName
```

The output should look something like this:

'img'

Lastly, try a search for a particular type of image.  In this example we'll start with a Publisher search, then we'll choose 'Canonical' from the list that's returned, and then we'll drill down into the SKUs of one of the Canonical offers.

All publisher list:

```
Get-AzureRmVMImagePublisher -l northeurope | Select PublisherName
```

Canonical's offers list:

```
Get-AzureRmVMImageOffer -l northeurope -Publisher Canonical | Select offer
```

1 x Canonical offer's SKU list:

```
Get-AzureRmVMImageSku -l northeurope -Publisher Canonical -Offer ? | Select Skus
```

<br>
#### Step 6 - Inspect the VM images available in all Regions using Azure CLI

Switch the Cloud Shell to Bash mode:

'img'

Enter the following in the Cloud Shell:

```
az vm image list --all -o table
```

az vm list-skus -l northeurope -o table ?

You should see the same differences as when using PowerShell.

Lastly, use the search function:

```
az vm image list --offer Ubuntu --all -output table
```

<br><br>
## Exercise 2 - Azure Marketplace

To view the Azure Marketplace that provides an index of full solutions that can be deployed on Azure please use a web browser of your choosing and visit:

```
https://azuremarketplace.microsoft.com/
```

Click on any of the offerings and inspect the options available to you.

'img'

<br><br>
## Exercise 3 - Provisioning a single Windows Server VM

We will now provision a single Windows Server VM twice.  The first time will be with an unmanaged disk.  The second time will be with a managed disk.

<br><br>
#### Step 1 - Return to/open the PowerShell IDE application


<br><br>
#### Step 2 - Download the PowerShell commands and edit to suit a configuration that maps to your own environment





<br><br>
### View ARM template before submit

<br><br>
### Disks vs. Managed Disks


<br><br><br>
## Exercise 4 - VM Agent and Extensions

<br><br>
### Configuration Management Tooling


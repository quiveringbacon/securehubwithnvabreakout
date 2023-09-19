# Securehub with nva breakout

This creates a vwan with a securehub and a couple of spoke vnets with VM's and an NVA vnet all connected to the vhub. All internet traffic is pointed to the Azure firewall in the hub. A specific subnet (8.8.8.8/32) it sent to a spoke NVA (in this case another Azure Firewall). This also creates a log analytics workspace and diagnostic settings for the firewall logs. You'll be prompted for the resource group name, location where you want the resources created, your public ip and username and password to use for the VM's. NSG's are placed on the default subnets of each vnet allowing RDP access from your public ip and route tables are added sending traffic to your public ip to the internet. This also creates a logic app that will delete the resource group in 24hrs.

The topology will look like this:
![wvanlabsecurehubwithspokefw](https://github.com/quiveringbacon/securehubwithnvabreakout/assets/128983862/4ff05cd2-4e31-4956-9de9-47b200baf5ad)

You can run Terraform right from the Azure cloud shell by cloning this git repository with "git clone https://github.com/quiveringbacon/AzureVwanlabwithSpokeFW.git ./terraform".

Then, "cd terraform" then, "terraform init" and finally "terraform apply -auto-approve" to deploy.

---
title: "Virtualbox Related Question"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by sdbpastor on 2010-02-01
I am rnning Ubunto 9.10 on my notebook pc and I can see and access my files in my Windows home network. I hvae used Virtualbox the create three virtual macines, Xubuntu, Kubunto and Vista Ultimate.

All three connect to the internet just fine. However, on neither of them can I see my Windows network and/or each other. I am assuming it is because I don't know how to configure the settings for the network in the virtual machines.

Can someone tell how to configure the virtual machines so that they can see and access my files on the Windows home network. Currently neither of he virtual machines even see the network but I do have wireless internet access.

Any help would be most appreciated.

Thanks,
Michael

PS
Another Virtualbox question. I'd like Virtualbox to automaticall open in a different workspace the the first one when launched. Can this be done? Even better, is there a way to have each virtual machine open in a specific workspace?

Thanks again,
Michael

---

### Post by suseendran.rengabashyam on 2010-02-02
Hi,

My guess is your guest machines network interfaces are using NAT to connect to the internet so you will not be able to browse your Windows file shares however you should be able to access your Windows shares availbale on your home network by using the url

smb://<ip_address>/<share_name>

in Nautilus.

Similarly you can also mount the shares using 'smbmount'.

Incoming connections to shares on your VMs will not work though. For that to work, you need to change the network interfaces connection method to Bridged. Please follow these steps to do the same:

1) Power Off your Virtual Machine

2) Right Click on your Virtual Machine->Settings->Network->Adapter 1

3) Check "Enable Network Adapter"

4) "Attached to:", change it to Bridged Adapter and click "Ok".

5) Power On your Virtual Machine and see whether you are able to access the Windows share.

---


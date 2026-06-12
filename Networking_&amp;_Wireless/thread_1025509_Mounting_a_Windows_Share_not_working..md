---
title: "Mounting a Windows Share not working."
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by itconstruct on 2008-12-30
I have tried various different methods for mounting a share on my windows xp professional machine which is on an active directory network. I have full access to the active directory domain and the ubuntu 8.10.1 machine.

I have tried the connect to server link and typed in all the details for my windows share but then I am told that it can't mount the share.

I have also tried using various online tutorials and have also tried using smb4k to no avail.

I can try accessing other shares if it is a problem with the setup with this particular xp machine as it is a virtual machine on virtualbox ose on my ubuntu laptop.

Can someone please tell me how I can access this share.

Any help would be greatly appreciated.

Please note I am not well versed with the ubuntu terminal but have some minimal understanding of it and it's functionality.

---

### Post by regala on 2008-12-30
> **itconstruct said:**
> I have tried various different methods for mounting a share on my windows xp professional machine which is on an active directory network. I have full access to the active directory domain and the ubuntu 8.10.1 machine.

I have tried the connect to server link and typed in all the details for my windows share but then I am told that it can't mount the share.

I have also tried using various online tutorials and have also tried using smb4k to no avail.

I can try accessing other shares if it is a problem with the setup with this particular xp machine as it is a virtual machine on virtualbox ose on my ubuntu laptop.

Can someone please tell me how I can access this share.

Any help would be greatly appreciated.

Please note I am not well versed with the ubuntu terminal but have some minimal understanding of it and it's functionality.

can you tell us what you tried that did not work ?
regards

---

### Post by itconstruct on 2009-01-03
I found out that the issue is due to a bug with VirtualBox. VirtualBox when you go devicees-> install guest additions tries to attempt to download the necessary package to install the guest additions but in my case the package wouldn't download as it was saying that the connection timed out. I clicked on the link, had to download the .iso file manually and then mount the image manually myself by clicking deices->mount cd/dvd-rom-> cd/dvd-rom image-> click add-> navigate and find necessary .iso folder on computer and then click open and select. You should then be able to run the guest additions setup and then you should be able to share files etc between host and guest OS after a restart of the guest machine.

---


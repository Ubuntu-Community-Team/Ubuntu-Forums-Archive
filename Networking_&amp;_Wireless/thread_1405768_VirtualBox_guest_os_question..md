---
title: "VirtualBox guest os question."
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by voncloft on 2010-02-13
I currently have VirtualBox installed on my Ubuntu 9.10 Desktop.  I have windows xp as a guest os and it has network shares on it.  My question is, is there a way for another computer to access those network drives on the guest os in virtualbox?

I don't want to search for hours on end on google, a simple no would be fine - however if it is possible let me know because when I am in windows on another computer that has windows as a host os it sees it in the windows network folder but it says "....network location not found" or something similar but it still shows a pc picture of the virtual os of the virtual box program running in ubuntu.

---

### Post by suseendranrb on 2010-02-13
Hi,

My guess is your Windows XP VM network interfaces are configured to use NAT so incoming connections to shares on your VMs will not work. For that to work, you need to change the network interfaces connection method to Bridged. Please follow these steps to do the same:

1) Power Off your Virtual Machine

2) Right Click on your Virtual Machine->Settings->Network->Adapter 1

3) Check "Enable Network Adapter"

4) "Attached to:", change it to Bridged Adapter and click "Ok".

5) Power on your Virtual Machine and see whether you are able to access the share. 

Let me know if it helps.

---


---
title: "Fresh Dapper Drake Install and Netgear WG111"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by hise0001 on 2006-07-08
I just did a fresh install of Dapper Drake and found that it recognized by USB network adaptor (Netgear WG111).  When I go to Administration->Networking I see that Wireless Ethernet eth1 is active; but, I can't ping my router.

Looking at the wiki on wireless adaptor, it appears that the WG111 is listed as not working out of the box and needs ndiswrapper to work.

I followed the ndiswrapper how-to to install my drivers (which is what I used to use when I was using Ubuntu 5.... which worked sporatically; but, that's a different story).

The interesting thing is that after the fresh install of Dapper, it recognized my wireless adaptor (even though it didn't work) and it recognized it without ndiswrapper being installed.

So, is there some step I can take to uninstall whatever Dapper may being using to recognize my wireless adaptor, and then I can go through the ndiswrapper setup and configuration?

Thanks for any feedback.

--Hise

---

### Post by bigken on 2006-07-08
try this open a terminal and type 
sudo gedit /etc/modprobe.d/options
add line: options acx firmware_ver=1.2.1.0.30;)

this worked for me on a netgear 311 v2

---

### Post by eternalsword on 2006-07-13
could you post the result of lsmod

---


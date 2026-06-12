---
title: "wirless problem"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by med linux on 2011-06-26
good morning 
I have hp q 610
ubuntu 10.10 can't detecte wirless 
whatshould i do ??

---

### Post by nm_geo on 2011-06-26
> **med linux said:**
> good morning 
I have hp q 610
ubuntu 10.10 can't detecte wirless 
whatshould i do ??

A few questions ..
Do you have an ethernet cable to connect with?
Have you updated your Maverick 10.10?

open terminal Applications>Accessories>Terminal

Copy and paste the following in terminal one at a time..enter
```
lspci -nn
``````
sudo lshw -C network
``````
rfkill list all
``````
lsmod
```Paste the results here and someone will have enough to get started with you.

---

### Post by MaindotC on 2011-06-26
The first place to start is the Ubuntu Wireless Troubleshooting Guide.  In order for your device to work properly you need the physical connectivity (plugged in all the way and/or turned on via your machine's BIOS), a driver to communicate between the device and the operating system, and then the proper configuration of the device which typically is via DHCP.  Please follow the guide and indicate at what point you are having difficulty.

---


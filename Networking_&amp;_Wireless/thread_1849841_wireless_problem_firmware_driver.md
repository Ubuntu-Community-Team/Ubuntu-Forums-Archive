---
title: "wireless problem firmware? driver?"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by kimyaman on 2011-09-25
Hi!

I have installed Ubuntu 11.04 on my laptop. For some reason Wireless  Network does not work, only LAN cable connection works.



lspci says:

**Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**




System->Administration->Additional Drivers doesn't list anything.

Can anybody help me? Thanks for any suggestions

---

### Post by wildmanne39 on 2011-09-25
Hi, run this command please then disconnect you wired connection after it is finished and restart your computer.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Now it should be working if so please use thread tools and mark as solved.
Thank you

---

### Post by kimyaman on 2011-09-27
i tried it and no result.
anything else? 
thanks

---

### Post by wildmanne39 on 2011-09-27
Hi, please post the results of these commands.
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
sudo iwlist scan
```
```
dmesg | egrep 'b43|firm|wlan0'
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---


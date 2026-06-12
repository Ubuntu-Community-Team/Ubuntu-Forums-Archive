---
title: "Dell 1720 wifi problem"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by aviator1 on 2011-09-04
Hello All:

I just installed 11.04 as a second OS on my Dell 1720. It boots and operates fine, but no wifi.

I have the broadcom unit in the computer.

What do I need to tweak to get operational.

I am only a Linux user, not a programmer type, so please be very basic when you respond.

Regards,

Dave

---

### Post by wildmanne39 on 2011-09-04
Hi, please run these commands and post the results here:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
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
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---


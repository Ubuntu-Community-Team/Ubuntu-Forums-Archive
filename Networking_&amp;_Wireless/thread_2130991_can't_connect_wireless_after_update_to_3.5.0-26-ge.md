---
title: "can't connect wireless after update to 3.5.0-26-generic"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by nimirooyn on 2013-03-31
leptop- toshiba sattelite l650
network cards are atheros(wired) and brodcome(wireless)
if I return to 3.5.0-17 all work fine... but it means I can't update and upgrade without wireless going haywire

now it gives me this- iwconfig
eth0 no wireless extensions
lo no wireless extensions

anyone encountered it?
tried to find help via google and all kinda places... some thing helped buy then everything got stuck and ubuntu got internal error.

help? XD

TY

Nimirooyn

P.s
any other info needed- will be provided :)

---

### Post by chili555 on 2013-03-31
Let's find out exactly which brodcome you have. Please open a terminal and run and post:```
lspci -nn -d 14E4:
```Thanks.

---

### Post by nimirooyn on 2013-03-31
I'll shorten it cause I'm working on 2 computers at a time XD
Broadcom Corp BCM4313 802.11b/g/n - - - (14e4:4727)

---

### Post by chili555 on 2013-03-31
The correct driver for your device 14e4:4727 is the Broadcom STA driver provided by bcmwl-kernel-source. Can you load the module?```
sudo modprobe wl
```If there is an error, re-install the driver with a temporary ethernet connection:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Now is it working?

---

### Post by nimirooyn on 2013-03-31
nop.... "fatal: module wl not found"

---

### Post by chili555 on 2013-03-31
> **nimirooyn said:**
> nop.... "fatal: module wl not found"As we expected. Please proceed with the next steps.

---

### Post by nimirooyn on 2013-04-04
that after the next steps :\
I think it's because I have no wired connection.... I reacon it needs some internet connection to run the commands ....

---

### Post by nimirooyn on 2013-06-22
well- just an update- 
version 13.04 solved the problem entirely
thanks for the help!

---


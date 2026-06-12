---
title: "Ubuntu can't detect Sony K550i using USB"
date: 2009-05-24
forum: Multimedia Software
---

### Post by thegeekin on 2009-05-24
I connected my Sony K550i using the USB Cable - I have installed Ubuntu 9.04 - OS does not recognize the phone anywhere. I can not find the phone in the "Places" menu nor under /media dir.

Wammu fails to recognize the phone due to obvious reasons. What can be the problem ?

---

### Post by xc3RnbFO8P on 2009-05-24
In Terminal, show the output of:
> lsusb

---

### Post by thegeekin on 2009-05-25
home@home-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046e:5542 Behavior Tech. Computer Corp.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0fce:d069 Sony Ericsson Mobile Communications AB
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---


---
title: "camera undetectable"
date: 2013-12-04
forum: Multimedia Software
---

### Post by vardavanderwieken on 2013-12-04
I have a msi wind netbook with an internal camera. I have ubuntu 12-latest version. and currently my camera goes missing. Fn 6 does not work. could someone please help me to activate it?

---

### Post by mörgæs on 2013-12-04
Ubuntu 12 is not the latest; 13.10 is. How does it work in a live boot of this one? 

Also please post the output of **lsusb**.

---

### Post by vardavanderwieken on 2013-12-04
is it adisavble to upgrade to ubuuntu 13

here is the output
lsusb
varda@varda-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 001 Device 005: ID 5986:02c1 Acer, Inc 
varda@varda-laptop:~$

---

### Post by mörgæs on 2013-12-04
> **vardavanderwieken said:**
> is it adisavble to upgrade to ubuuntu 13


You tell me. Again, how does the live boot work? 

There was a regression for the [5986:02c1]("http://permalink.gmane.org/gmane.linux.usb.general/65562") camera. Might be fixed in 13.10.

---


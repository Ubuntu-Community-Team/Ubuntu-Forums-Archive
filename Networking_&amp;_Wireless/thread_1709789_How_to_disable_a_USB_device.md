---
title: "How to disable a USB device?"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by almikul on 2011-03-18
I have a dual boot Ubuntu 10.04 / Win 7. I have two wireless adapters connected to desktop - one works for Windows, one works for Ubuntu. For Windows, it is not a problem - it cannot find a driver, so it ignores the device. In Ubuntu, however, there is a driver that does not work properly but loads anyway and messes up the whole wireless connection. So, Ubuntu sees two wireless adapters and mounts both of them.

Here is the question: how can I permanently disable a USB device upon start up? Ideally, both coldplugs and hotplugs should not work, but at least coldplug should be disabled.

Any suggestions would be appreciated.

---

### Post by chili555 on 2011-03-19
> there is a driver that does not work properly but loads anywayYou can blacklist the driver. For example:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist baddriver
```Proofread. save and close gedit.

---

### Post by almikul on 2011-03-19
> **chili555 said:**
> You can blacklist the driver. For example:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist baddriver
```Proofread. save and close gedit.
Thank you. I did it already, but for some reason sometimes I can still see the second adapter in the Network Manager menu. 

I would still prefer to know how to disable the entire device.

---

### Post by chili555 on 2011-03-19
> I did it already, but for some reason sometimes I can still see the second adapter in the Network Manager menu.Did you blacklist all the modules that depend on, and load anyway, the module you blacklisted? If the module doesn't load, *as well as its dependencies*, believe me, you will not have a working interface.

I am afraid to ask, but what is blacklisted and what doesn't work about it?

---

### Post by almikul on 2011-03-19
> **chili555 said:**
> Did you blacklist all the modules that depend on, and load anyway, the module you blacklisted?
I am not really sure because I deducted what modules needed to blacklisted by inspecting the output of *lsmod*. I may have skipped something.

> I am afraid to ask, but what is blacklisted and what doesn't work about it?
It is a cheap usb wireless adapter that does not even display the brand or model on the case.  Here is what it shows:
```
~$ lsusb
Bus 007 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 007 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:7611 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

It is Ralink one I am trying to disable, so I blacklisted *rt2870sta*. I think it depended on something, but I haven't looked closely. Now this module does not load, but at least once after restarting I still could see the adapter in Network Manager. At the moment, however, it does not show.

---

### Post by chili555 on 2011-03-19
You were close, but an essential piece of information is missing. Your device is claimed by both rt2870sta and rt2800usb leading to conflicts and lousy performance. If you want to get the Ralink to work a lot better, maybe good enough to satisfy you, then amend your files:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Remove any reference to blacklist rt2870sta and add:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Now remove the Linksys and reboot. Does the Ralink work as expected?

---

### Post by almikul on 2011-03-20
chili, thank you very much for your help. Now, Ralink works like a charm :)

---


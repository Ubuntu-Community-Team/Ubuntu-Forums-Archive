---
title: "Problems installing Wireless USB Adapter: Belkin FD4050"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by robert walker on 2010-04-11
I am not managing to configure a wireles newtwork.  I am offline (with an online laptop  to help me)
I am new to Ubuntu and am running Ubuntu 10.04 ... only because for some reason that is the only version that will load onto my IBM pentium 4 desktop!
I installed ndisgtk, ndiswrapper-common and ndiswrapper-utils-1.9  by using the Synaptic Package Manager GUI.
Using Windows Wireless Drivers GUI, I installed the driver rt 2870 off the Belkin CD that came with the product. Status is "Hardware present: Yes"

here is the status of my lsusb and iwconfig:
------------------------------------------------------------------

finn@finn-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 050d:935a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

--------------------------------------------------------------------

finn@finn-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

--------------------------------------------------------------------

It seems I have ndiswrapper working (I think!) ... but i still can't connect my wireless.  Where do I go to from here?
Help!

---

### Post by chili555 on 2010-04-11
Ndiswrapper may, or may not be the best method. Let's take a look at:```
ndiswrapper -l
dmesg | grep ndiswrapper
```Thanks.

---


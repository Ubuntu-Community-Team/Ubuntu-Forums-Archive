---
title: "Help with netgear wg111t......"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by pooptoof on 2009-07-21
Help please with netgear wg111t....

I've installed the drivers athfmwdl.inf and netwg11t.inf using ndiswrapper. the device shows up as present in ndiswrapper. However, no wireless connection shows up in network admin. here's the output of of lsusb and iwconfig....


ivan@ivan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ivan@ivan-desktop:~$ lsusb
Bus 002 Device 002: ID 1385:4250 Netgear, Inc WG111T
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 03f0:4f11 Hewlett-Packard Officejet 5600 (USBHUB)
Bus 007 Device 002: ID 04f2:0618 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ivan@ivan-desktop:~$ 




I don't seem to have anything for wlan0



any thoughts?

---

### Post by superprash2003 on 2009-07-21
[https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T) did you follow step 7 ?

---

### Post by pooptoof on 2009-07-24
Ok. I tried all that, including adding the line ndiswrapper to /etc/modules. At first it seemed like we might be getting somewhere. I actually saw a wireless connection in network manager for the first time. and ndis saw the hardware as present. I added the line to /etc/modules and now I got nothing. Won't detect the hardware, nothing. any ideas?

---

### Post by pooptoof on 2009-07-24
Additionally, I was able to get wireless up and running again, but only after uninstalling the drivers, restarting the computer, and reinstalling them. Again, all this went away after I rebooted Ubuntu.

---

### Post by pooptoof on 2009-07-24
to the top please......

---


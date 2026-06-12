---
title: "Belkin Driver Troubles"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by den160593 on 2009-01-06
Hi,

I have a wireless Belkin Driver (F5D7000au), however I don't know how to install it to make it work. I try and run the autorun.inf thing to install the driver, but it doesn't work at all (I have looked here [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin) however I can't fix my problem.

Could anyone help me here? On how to install it / get my wireless internet to work? This router works perfectly well on windows. This is all on the 8.10 version of Ubuntu

Thanks heaps
-Den

---

### Post by den160593 on 2009-01-06
I did some more looking around and my driver is a bcmwl5.inf

How would i be able to install this?

---

### Post by den160593 on 2009-01-06
Ok I managed to install the driver but my net on Ubuntu still doesn't work:

denis@denis:~$  ndiswrapper -l
autorun : invalid driver!
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
denis@denis:~$ ndiswrapper -i $/media/Belkin_F5D7000au/Driver/bcmwl5.inf
driver bcmwl5 is already installed

*-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:30:bd:f6:50:44
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


Can anyone help?

---


---
title: "ndiswrapper - WEP vs WPA - WPA not working"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by Dekafox on 2013-06-15
I've got a Netgear N600 USB wireless adapter that I got working with ndiswrapper.  It can connect to WEP networks, but if I try to join a network wiht WPA, it keeps failing(though it takes a minute or so) and re-prompting for the password.  I've run a couple diagnostics already.  When I try connecting, it's obviously trying WPA2 properly:
```
root@Battlenizer:/etc/wpa_supplicant# sudo iwlist wlan0 auth
wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		WPA2
          Current Key management :
		PSK
          Current Pairwise cipher :
		CCMP
          Current Pairwise cipher :
		CCMP
          Current Authentication algorithm :
		open

```

And it shows it's capable of this too, so it doesn't appear to be a driver issue.  dmesg doens't show anything for the connection attempts unfortunately

---

### Post by praseodym on 2013-06-16
Do you really need ndiswrapper? Please show

```
lsusb
```

---

### Post by Dekafox on 2013-06-16
```
root@Battlenizer:/var/log# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. Serial-ATA bridge
Bus 002 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 003 Device 002: ID 19ff:0219 Dynex 
root@Battlenizer:/var/log# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmn43xx64 : driver installed
	device (0846:9011) present

```

I tried it wihtout ndiswrapper at first, but got nowhere, and every mention I found of using this device says they only got it working through ndiswrapper.

---

### Post by praseodym on 2013-06-16
Try to change the router to b/g mode only.

---

### Post by Dekafox on 2013-06-16
It didn't work.  I want to be using n though with this device anyways, since it'll be for streaming media, and it's the reason I even got this one in the first place(since it supports n).  It is in general mixed mode right now(since I have a laptop that has a G adapter).

*edit* I also tried kicking it over to the 5GHz band and that had the same symptoms.

---

### Post by Dekafox on 2013-06-17
Any other suggestions?  I'd prefer not to have to go buy something else to make this work...

---


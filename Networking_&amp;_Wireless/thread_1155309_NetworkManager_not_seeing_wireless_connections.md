---
title: "NetworkManager not seeing wireless connections"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by Thundara on 2009-05-10
This morning jaunty decided to act up on me and the computer has been out of internet since. Originally, the internet had lost connection without realizing it, so I tried having the NetworkManager applet in GNOME disable wireless and re-enable it, but afterward it was unable to locate any internet sources, even when using the "Connect to hidden network..." feature. Trying to connect through the command line hasn't worked either, so I'm wondering if anyone knows of any solution to my problem or has encountered it themselves?

Here's the system info:
**Brand:**
```
Dell Inspiron 1150
```
**lsb_release -d:**
```
Description: Ubuntu 9.04
```
**uname -mr:**
```
2.6.28-11-generic i686
```
**lspci:**
```
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wrieless LAN Controller [14e4:4320] (rev 03)
```
**lshw:**
```
*-network:0
	description: Ethernet interface
	product: BCM4401 100Base-T
	physical id: 1
	bus info: pci@0000:02:01.0
	logical name: eth0
	version: 01
	serial: 00:0f:1f:18:e9:81
	size: 10MB/s
	capacity: 100MB/s
	width: 32 bits
	clock: 33MHz
	capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
	configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latnecy=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
*-network:1
	description: Network controller
	product: BCM4306 802.11b/g Wireless LAN Controller
	vendor: Broadcom Corporation
	physcial id: 2
	bus info: pci@0000:02:02.0
	version: 03
	width: 32 bits
	clock: 33MHz
	capabilities: bus_master
	configuration: driver=b43-pci-bridge latency=32 module=ssb
*=nework
	description: Wireless interface
	physcial id: 2
	logical name: wlan0
	serial 00:90:96:b5:a7:e7
	capabilities: ethernet physcial wireless
	configuration broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by x22 on 2009-05-10
looks like an ndiswrapper case: see URL

[http://www.melbpc.org.au/pcupdate/2407/2407article12.htm](http://www.melbpc.org.au/pcupdate/2407/2407article12.htm)

---

### Post by Thundara on 2009-05-10
> **x22 said:**
> looks like an ndiswrapper case: see URL

[http://www.melbpc.org.au/pcupdate/2407/2407article12.htm](http://www.melbpc.org.au/pcupdate/2407/2407article12.htm)
It's been working without ndiswrapper for months though, only started malfunctioning today

Edit: Magic, suddenly it works again...weird...All I did was "sudo killall nm-system-settings" and restart...

---

### Post by Egi_Power on 2009-05-11
Hi!

I just had a very similar issue, which is now sorted out with the help from **chili555**.
You can find the link here to my post, just in case your wireless goes down again.

[ipw2200 problems in Hardy]("http://ubuntuforums.org/showthread.php?t=1154721")

Best regards,

Egi_Power

---


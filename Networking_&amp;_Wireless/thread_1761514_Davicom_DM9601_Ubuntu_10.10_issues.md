---
title: "Davicom DM9601 Ubuntu 10.10 issues"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by koyo23 on 2011-05-18
Hi i have a USB Davicom DM9601 network adapter but does not work. Can some1 who has a working 1 please post their work around? or please post the driver so that i can recompile for my machine. Thank you.

---

### Post by chili555 on 2011-05-18
i am nt 1 who has a workin 1 but pls open a terminal and try:```
sudo modprobe dm9601
```Does your ethernet come to life? If not, please run and post:```
dmesg | grep dm9
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by koyo23 on 2011-05-19
[   16.717869] usbcore: registered new interface driver dm9601
[  445.975677] dm9601 1-4.1:1.0: eth1: register 'dm9601' at usb-0000:00:1d.7-4.1, Davicom DM9601 USB Ethernet, 00:60:6e:30:06:3e


I have the interface list but when i try to use it nothing happens.

---

### Post by chili555 on 2011-05-19
> I have the interface list but when i try to use it nothing happens.Please show us:```
ifconfig
```Is Wired Network available when you click the Network Manager icon? Does it try to connect?

---

### Post by koyo23 on 2011-05-20
eth1      Link encap:Ethernet  HWaddr 00:60:6e:30:06:3e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

i do have the icon, but its grayed out when i plug in a cable it does not light up.

---

### Post by chili555 on 2011-05-20
With the cable plugged in, please run and post:```
sudo ethtool eth1
```

---

### Post by koyo23 on 2011-05-21
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000007 (7)
	Link detected: no

---

### Post by chili555 on 2011-05-21
> Link detected: noIt doesn't think there is a cable and a router attached. That is consistent with "when i plug in a cable it does not light up." Are you certain the cable and router are sound? If so, I am not sure I have any other ideas.

---

### Post by koyo23 on 2011-05-21
theres no issues with the cable and router. :(

---

### Post by indistinguishible on 2011-07-28
Exactly the same problem. Even the same ethtool and dmesg output. When I plug in the cable it starts to blink moderatly but that's all. Sometimes in network manager it allows me to choose my "Auto eth0" connection but after 30 seconds it's shows "Wired network disconnected" message.
Any ideas?

---

### Post by hyperair on 2011-08-07
This adapter seems rather picky the devices it supports. It can detect a link when I connect a cable from it to the integrated ethernet ports of my Ideapad and Thinkpad, but not when I connect a cable from it to the ethernet port in my university room.

---

### Post by hackeron on 2012-07-31
root@miniand:~# modprobe dm9601
FATAL: Module dm9601 not found.

Hmm?

I'm on Ubuntu 12.04 LTS

---

### Post by chili555 on 2012-07-31
Hmmmm, indeed. It's on my 12.04 system:> $ modinfo dm9601
filename:       /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/usb/dm9601.ko
license:        GPL
description:    Davicom DM9601 USB 1.1 ethernet devices
<snip>Please run and post:```
ls /lib/modules/`uname -r`/kernel/drivers/net/usb/
```Those tickmarks are on the left side of my US keyboard on the same key with ~. Thanks.

---

### Post by hackeron on 2012-08-01
> **chili555 said:**
> Hmmmm, indeed. It's on my 12.04 system:Please run and post:```
ls /lib/modules/`uname -r`/kernel/drivers/net/usb/
```Those tickmarks are on the left side of my US keyboard on the same key with ~. Thanks.

```

# ls /lib/modules/`uname -r`/kernel/drivers/net/usb/
ls: cannot access /lib/modules/3.0.36-t1+/kernel/drivers/net/usb/: No such file or directory

```

I guess that would be why :) - I'm using a Lubuntu distribution running on an MK802 from miniand.com - I'm guessing they didn't compile USB networking in :(

---


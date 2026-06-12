---
title: "WiFi that used to work under Breezy"
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by Arctic Patrol on 2006-01-02
Hi everyone,

I'm having a great time with Ubuntu but there is something that's been driving me mad lately. I use a BT Voyager 1065 WLAN PC card on Samsung V25 notebook. It's going into a BT Voyager 2100. On the security front I've got a wep key and a hidden ESSID. The card is recognized as a network interface thanks to ndiswrapper but I can't access my network anymore.

The thing is, until I had to reinstall the whole after I'd done something stupid, it used to work. I've tried to enter the password in ascii with the s: prefix but without much luck. I reverted to hex as it's how it used to work. I've tried all the possible combinations with the network configuration GUI but that didn't work either.

Here's my etc/network/interfaces, hoping one of you will see something obvious.

> 
auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Jungle
wireless-mode managed
wireless-key1 62726669756C696D6739333731
wireless-defaultkey 1
wireless-channel 5

auto eth0


---

### Post by buttyshell on 2007-02-26
I have just switched from windblows xp to unbunto and habe a BT Voyager 1065 PCMIA card but I cant get ubunto to recognise this device how do I get a good driver so i can set up  my wireless?

---


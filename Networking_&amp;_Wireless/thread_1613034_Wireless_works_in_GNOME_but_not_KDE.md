---
title: "Wireless works in GNOME but not KDE"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by mortalapeman on 2010-11-03
I know my pass phrase, I know my encryption type, I put that info into the wireless utility for GNOME and it works. I Just recently installed the Kubuntu desktop from the repos and tried to connect to my internet wirelessly and for some reason it can't establish a connection. Is there some option I don't know about that was being set for me automatically before?

Here is my wireless info:

id:	
network
description:	Wireless interface
product:	RTL8187SE Wireless LAN Controller
vendor:	Realtek Semiconductor Co., Ltd.
physical id:	
0
bus info:	
pci@0000:0e:00.0
logical name:	
wlan0
version:	22
width:	32 bits
clock:	33MHz
capabilities:	pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	r8180
latency	=	0
multicast	=	yes
wireless	=	802.11b/g link
resources:	
irq	:	18
ioport	:	a000(size=256)
memory	:	f0200000-f0203fff

Any ideas?

---

### Post by mortalapeman on 2010-11-05
The network manager is running as root, which I'm pretty sure it is supose to be, when I log into the KDE desktop. I know that GNOME uses the network manager applet and KDE uses the actual network manager. I looked at the process in the system monitor for the network manager and tried to see if it was taking up CPU time while it tried to connect in KDE but it said the process was sleeping.

I think the network manager in KDE might not be talking to something the right way, anyone have any clues?

---


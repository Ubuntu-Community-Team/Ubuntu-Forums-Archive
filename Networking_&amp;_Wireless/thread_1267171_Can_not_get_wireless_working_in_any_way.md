---
title: "Can not get wireless working in any way"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by dirty_von_Shotgun on 2009-09-15
I used to use a wired connection but I moved and no can only use wireless however I cannot in any way get it to work in Jaunty.

I've followed a bunch of different guides and still nothing. I'm currently in Vista :( because the internet will work.

I use a Marvell Libertas PCI wireless adapter. I do not think NDISWrapper is working. I've also tried to configure the wireless but every guide I've found says use "Network Manager" which I can't find in Jaunty. I remember it from Intrepid. I'm out of ideas and really don't want to have to abandon Ubuntu because of this.

Edit: Every guide I've tried for NDISWrapper says my card should come up as wlan0. It comes up as wlan1, however the card itself is not actually on.

---

### Post by Cuba71 on 2009-09-15
You're not describing the model of your Marvel PCA wireless adapter, but just in case, I'm attaching a zip file with the Windows drivers for the Marvel 88w8355, [11ab:1faa] and a README file with instructions on how to install ndistgk (ndiswrapper GUI) and the drivers.

Make sure your adapter is the same model and same Vendor ID/Product ID.

Good luck

---

### Post by dirty_von_Shotgun on 2009-09-15
All windows device manager says is "Marvel Libertas 802.11 b/g Wireless LAN Client Adapter"

I'll check this out though. Thanks

Edit: I do not see your attached file.

---

### Post by Cuba71 on 2009-09-15
To find the Vendor ID and Product ID under windows, go to Device Manager, expand your Network Devices, right click on the wireless adapter and under the Detail Tab you'll see a line like this:

   PCI\VEN_11AB&DEV_1FAA . . . . . . . .

that gives you [11ab:1faa] the VID&PID

To obtain that info in Ubuntu, type the command: lspci -nn

I apologize for missing the attachment, here it goes

---

### Post by dirty_von_Shotgun on 2009-09-15
There is one problem with your walkthrough. I cannot connect to the internet so I won't be able to use Synaptic. Is there a link where I can d/l a .deb (or anything) to install ndistgk?

---

### Post by dirty_von_Shotgun on 2009-09-15
Found a link, I'll give this a shot after work.

---

### Post by Cuba71 on 2009-09-15
It's possible that ndisgtk is already in your Synaptic database and you won't have to be on-line to install it.
I'm also attaching the .deb package to this post.

---

### Post by dirty_von_Shotgun on 2009-09-17
So I don't appear to be able to do anything and I think it is because I can't connect. I tried installing from .deb and it just exits. I tried from the repository and it hangs and I can't even access synaptic. This is really becoming a pain. Has anyone dealt with this before?

---

### Post by Iowan on 2009-09-17
You can see what (if anything) Ubuntu thinks of your card by entering (from a terminal)```
lshw -C network
```

---

### Post by dirty_von_Shotgun on 2009-09-17
> **Iowan said:**
> You can see what (if anything) Ubuntu thinks of your card by entering (from a terminal)```
lshw -C network
```

*-network:0 UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 3
bus info: pci@0000:02:03.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list
configuration: latency=32


*-network:1
description: Ethernet interface
product: 82562EZ 10/100 Ethernet Controller
vendor: Intel Corporation

physical id: 8

bus info: pci@0000:02:08.0
logical name: eth0

version: 01
serial: 00:0c:f1:ad:ee:46

size: 10MB/s

capacity: 100MB/s

width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A ip=192.168.1.136 latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s


*-network DISABLED

description: Ethernet interface
physical id: 1

logical name: pan0
serial: 6a:91:9f:89:cd:9d
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


I never had any problems with Ubuntu until upgrading to Jaunty. I may roll back because Jaunty has given more problems than the past 3 releases combined.

Edit: The card appears on here, but it does not turn on when I log into ubuntu. Also I have no idea how to set up a wireless connection in Jaunty. It was easy in the last two.

---


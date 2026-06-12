---
title: "Does NDISWRAPPER + DRIVER = FIRMWARE?"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by billplowman on 2011-02-14
Hi all,
 
So, I'm an absolute Linux novice trying to install Ubuntu 10.10 on 2 old laptops. One is a Panasonic Toughbook CF-48 and the other is a Dell Inspiron 1100. I had some issues with the GUI installer on both machines, so I went with the alternative text based installer, which seemed to work without a hitch.
 
The problem I'm having is with wireless networking. Neither machine has built-in wireless, so I'm using a Linksys WPC54G Wireless-G card. After installing the ndiswrapper packages and loading the Windows driver for the Linksys card on both machines, the Panasonic wireless is up and running. The Dell, however, is still telling me that the firmware is missing.
 
Now I think what's missing something is me! Is it possible that Ubuntu is not recognizing the PCMCIA slots on the Dell?
 
Any help would be greatly appreciated!
 
Thanks,
Bill

---

### Post by matt_symes on 2011-02-14
Hi

Open a terminal and type

```
ndiswrapper -l
```

That is a small L above. Does it say the driver is installed correctly ?

KInd regards

---

### Post by billplowman on 2011-02-14
Well, it looks like the driver is installed. If it's correct or not is another story.
 
lsbcmnds : driver installed
device (14E4:4318) present (alternate driver: ssb)
 
How does that look?

---

### Post by matt_symes on 2011-02-14
Hi

If that's the same driver that's installed on the other machine that machine is working and the cards are the same then that driver on the dell should be the correct one.

> The Dell, however, is still telling me that the firmware is missing.

When does it say that and what is the exact error message ?

Kind regards

---

### Post by billplowman on 2011-02-14
When I click on the network icon it says:
 
Wireless Networks
   device not ready (firmware missing)
 
Also, when I go into System > Administration > Network Tools and pull up wlan0, the State says Inactive.

---

### Post by dmizer on 2011-02-14
We'll need to know what chipset you use in the cards. Please post the output of:
```
lshw -C network
```

---

### Post by billplowman on 2011-02-15
Here is what I get:
 
WARNING: you should run this program as super-user.
*-network 
description: Ethernet interface
product: BCM4401 100Base-T
vendor: Broadcom Corporation
physical id: 1
bus info: pci@0000:02:01.0
logical name: eth0
version: 01
serial: 00:0d:56:b5:24:b3
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 multicast=yes
resources: irq:7 memory:fcffe000-fcffffff
*-network
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64
resources: irq:11 memory:f8000000-f8001fff
*-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:14:bf:99:c7:7a
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
&#12288;

---

### Post by romain.astie on 2011-02-21
Hey Guys,

I have the exact same Wireless Card, and been trying for two days to get my wireless up and runnning. Ubuntu still tells me that the firmware for the card is missing. How can I fix this? I am new to Ubuntu, and the wireless card is the only internet access I have. The computer I have is a Dell Latitude CPi... yeah I know it's old. For info, I'm using the same driver Josh has. THe error messages appear to be the same as well. HELP, ANYONE?...:popcorn:

---

### Post by dmizer on 2011-02-21
> **romain.astie said:**
> Hey Guys,

I have the exact same Wireless Card, and been trying for two days to get my wireless up and runnning. Ubuntu still tells me that the firmware for the card is missing. How can I fix this? I am new to Ubuntu, and the wireless card is the only internet access I have. The computer I have is a Dell Latitude CPi... yeah I know it's old. For info, I'm using the same driver Josh has. THe error messages appear to be the same as well. HELP, ANYONE?...:popcorn:

This has been solved in this thread: [http://ubuntuforums.org/showthread.php?t=1686679](http://ubuntuforums.org/showthread.php?t=1686679)

---

### Post by romain.astie on 2011-02-21
Thanks for the tips..
 But as in the other thread, my driver isn't there to activate. The list is blank... can I have any more help, please?

---

### Post by romain.astie on 2011-02-21
Never mind, my  wireless card just
 started working of it's own account...   Cool!

---


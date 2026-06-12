---
title: "Belkin F5D7330/Jaunty/Dell Dimension 4600 no connection, can't see device"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by sboisen on 2010-01-19
I'm trying to set up a wireless connection using a Belkin F5D7330 Ethernet bridge, an device that's at least 4 years old (so this isn't a card or a USB connection: it's attached via cat5). When i boot up, the Network manager spins for a while and then shows 4 stacked bars and a red X: no network connection. Wired network is greyed out. On right-click, Enable Networking is checked. On the bridge, the power light is on, and the ethernet connection light is yellow, indicating a 100Mbps connection. 

output from: sudo lshw -C network 
(... stuff about the Ethernet Controller)
*-network DISABLED
    description: Ethernet interface
    physical id: 1
    logical name: pan0
    serial: 42:54:8a:20:a0:90
    capabilities: ethernet physical
    configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

So there's no evidence i can find that the system even knows the hardware device is there. 

How do i diagnose this problem?

---

### Post by Iowan on 2010-01-20
The (... stuff about the Ethernet Controller) might be useful - in particular the driver. Are you connecting (or trying to) via wired or wireless? You mentioned "set up a wireless connection", but also "it's attached via cat5". 
Sorry, I'm dense...

---

### Post by sboisen on 2010-01-22
The Ubuntu box has a wired Ethernet connection to the Belkin device, which is a wireless bridge. The goal is for the bridge to connect via wireless to my in-house wireless router. But i can't see that the Belkin device is recognized by Ubuntu.

---

### Post by sboisen on 2010-01-23
I wanted to report back for future thread trolls: there was apparently no Ubuntu issue here at all. I stepped all the way back and tried the bridge on my Windows laptop, and had to reset several auto IP and DNS settings on the laptop and the wireless router i was trying to connect to. Once i got to where i could use the bridge to connect with laptop (that took a painfully long time), then simply connecting the device to the Ubuntu box worked just like it was supposed to.

---


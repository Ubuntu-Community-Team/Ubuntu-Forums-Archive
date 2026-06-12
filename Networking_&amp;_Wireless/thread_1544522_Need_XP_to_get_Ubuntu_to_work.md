---
title: "Need XP to get Ubuntu to work"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by thelugnut on 2010-08-02
SONY VGN-NS105N
Siemens SL2-141 router/modem
Ubuntu 10.04

I set up the wireless connection with no problems. Everything worked well.
I shut down the laptop and about two hours later turned everything back on. Everything appeared to be working, as the animated icon searched for the connection. A message popped up stating I was connected. But I could not access the Internet. in fact I couldn't even access the router-modem. I restarted the computer, and loaded Windows XP. I did the wi-fi search and made the connection. I accessed the Internet with no problems. I then restarted the thing again, and loaded Ubuntu 10.04. Everything worked just fine, including connecting to the Internet. To be sure I did this three consecutive times. If I shut down the computer, I have to start in Windows XP before I can access the Internet in Ubuntu. I think I have to enable something somewhere but just what, I don't know. Any thoughts?

---

### Post by Iowan on 2010-08-02
What are the results of **sudo lshw -C network** immediately after restart - and after the Windows trick. Sounds like a driver is being left active after the Windows trick - and it isn't there during normal reboot.

---

### Post by thelugnut on 2010-08-03
If I understood you correctly, this is the output AFTER I loaded Windows XP, connected to the Internet, then restarted the computer and loaded Ubuntu 10.04. Again, everything worked fine following the procedure.

```
*-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 13
       serial: 00:1d:ba:8a:57:0a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:d2d20000-d2d23fff ioport:d000(size=256) memory:d2d00000-d2d1ffff(prefetchable)
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:b6:33:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=10.0.0.1 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d0500000-d0501fff

```

---

### Post by thelugnut on 2010-08-03
Things got progressively worse and eventually Ubuntu 10.04 would noy even load. I cleared the partition and did a clean install and all is functioning normal.

---


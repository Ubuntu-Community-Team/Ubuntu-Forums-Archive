---
title: "atl2: eth0 NIC Link is Down"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by olskar on 2009-01-14
Hi, I am using wired internet over a speedtouchmodem from my asus EEE pc and I keep getting disconnected :(

Dmesg:
> [   38.449072] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.653366] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   38.655185] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   38.724220] NET: Registered protocol family 17
[   48.912022] eth0: no IPv6 routers present
[   81.823705] atl2: eth0 NIC Link is Down
[   83.457706] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   84.432654] atl2: eth0 NIC Link is Down
[   86.046095] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  177.711434] atl2: eth0 NIC Link is Down
[  179.312034] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  179.670216] atl2: eth0 NIC Link is Down
[  181.216628] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  231.439751] atl2: eth0 NIC Link is Down
[  234.294513] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  293.806830] atl2: eth0 NIC Link is Down
[  295.444457] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>



lspci:
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)



Any ideas?

---

### Post by cybrid on 2009-03-09
I have the very same problem, in fact I could paste the same dmesg log except for the card. I have tried with a Realtek PCI NIC and the one integrated in the motherboard, ending up with the same result. ¿Any ideas?.

---

### Post by cybrid on 2009-03-10
Nobody has the slightest idea?, not a clue?. What could we check/do to trace the problem?.

---

### Post by cybrid on 2009-03-10
A new clue, there is no light in the router's port and I have only managed to get the wired connection working when I use another machine that has Windows Vista X64 installed. My notebook also has ubuntu and the wired connection does not work either but luckily I can connect wirelessly.

I will try again this night by resetting the router to factory defaults.

---

### Post by cybrid on 2009-03-11
Eureka!!
The problem lies in my router, it is an all-in-one solution that has router, wifi access point and a DSL modem in one box. It seems that the switching capabilities of the router are broken, so the only way of getting a stable link between the server and the router is to set the link speed to 10Mb and turn off autonegotiation, all of witch can be accomplished with the following command (you must run it as root).

```
ethtool -s eth0 speed 10 duplex full autoneg off
```

---

### Post by Gauner_1 on 2010-01-03
Superb, thanks, That helped also with my same problem.

---

### Post by hotrod7262 on 2012-02-11
This helped me as well!  After hours of searching for an answer.  I have to set it to 10Mbs otherwise the connection toggles in and out continuously.  Have you found any router setting that helps fix this?

---


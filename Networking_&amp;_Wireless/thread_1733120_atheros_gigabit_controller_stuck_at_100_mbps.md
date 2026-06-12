---
title: "atheros gigabit controller stuck at 100 mbps"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by Helios747 on 2011-04-18
Hello,

I'm using Ubuntu Server 10.10 64 bit and am trying to get my Atheros AR81xx gigabit ethernet controller to use 1 gbps.

I have 2 ethernet controllers, one's a linksys 100 mbps (which is connected to the router which goes to the internet) and the other is the Atheros gigabit controller that is connected to a Windows desktop that has an NVIDIA gigabit ethernet controller (for faster file transfers with a gigabit connection)

I've ruled out that the problem is with the desktop as I plugged the windows PC into my macbook (which has a gigabit controller), and both the macbook and desktop report a gigabit connection.

I plug the windows desktop into the server and I only get 100 mbps.

I am using a Cat 6 patch cable. I've tried several methods with ethtool to force it into 1 gbps mode, but none work. I've tried using a different cable. no change. I've tried making windows force a 1 gbps connection, didn't have the option to in the driver configuration. Only 10/100 configs.

the commands I've tried in ethtool

```
ethtool -s eth0 speed 1000
```Reports no error, but no effect.

I've tried forcing off auto negotiation (I had a hunch it was causing the problem)

```
ethtool -s eth0 speed 1000 duplex full autoneg off
```I get this

```
Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex
  not setting autoneg

```I tried each setting individually, and autoneg won't set, the others will (but not do anything)


Is there anything I'm missing here? I would really like 1 gig speeds to my desktop. :)

---

### Post by Helios747 on 2011-04-19
gigabump

---

### Post by Helios747 on 2011-04-21
terabump

---

### Post by lakerssuperman on 2011-08-12
I too see this behavior on a few of my machines.  I try to set the speed with ethtool but it has no effect.  I transfer a lot of files across my home network and want to make sure I'm getting the best possible speed.  ethtool reports that my machines are capable of gigabit speed, I just can't seem to enable it.

---

### Post by Helios747 on 2011-08-12
Needless to say I've given up on this,  However 11.04 still has this problem. Just did a quick test.  If somebody could figure this out that would be fantastic.

---

### Post by xclusive585 on 2012-03-10
bringing-back-the-dead bump.

anyone? does anyone know if 12.04 will have this issue as well?

I guess the thing that puzzles me is, why there is apparently no proprietary driver available.

---

### Post by TuurEfe on 2012-04-18
Hi!

I'm having slightly different, but similar problem with my Atheros controller. It goes to 1000mb/s and in the gigabit switch, the light indicates the connection is 1000mb/s, but it network does not work (for example ping).
When I manually change it to 100mb/sec it will start working.

If I do a 
*lspci -vv*
I will get this info about my card:

02:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device 831c
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 44
    Region 0: Memory at fbdc0000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at cc00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ATL1E
    Kernel modules: atl1e

Does anyone have any idea why my card only really works at 100baseT or 10baseT, even though it seems to successfully negotiate 1000baseT? I'm having Asus M4A78T-E and 64bit installation. I tried updating the latest firmware, but that didn't help on the problem.

Anyway, back to the original problem, I'm not an expert on this, but just wondering:
Is your card showing the 1000baseT/Full in supported link modes? Mine does. It will probably not work unless you have 1000baseT listed. Might be that the 1000baseT will not work anyway, even if you get it enabled, if you have the same problem I have..

> *ethtool eth1*
Settings for eth1:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            **1000baseT/Full **
Supports auto-negotiation: Yes
    Advertised link modes:  1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x00000000 (0)
                   
    Link detected: yes

---

### Post by Helios747 on 2012-04-18
It turned out my card was mislabeled, it's not gigabit.

---


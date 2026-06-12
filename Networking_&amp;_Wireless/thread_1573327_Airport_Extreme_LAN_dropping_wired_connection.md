---
title: "Airport Extreme LAN dropping wired connection"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by unclecharlie on 2010-09-12
Hi all,

I'm running 10.04 64 bit and Windows 7 dual boot on an ASUS P7P55D motherboard.  I'm wired into an Apple Airport Extreme.

Ubuntu will not connect to the LAN on startup.  I have to unplug the power to the Airport (not a popular thing for me to do) and let it reset all connections.  Then it connects quickly.

If I stop on a website to read a long page, for let's say 5 minutes, the connection is lost but Ubuntu thinks I'm still connected.  If I click Auto Ethernet under the network connection icon it immediately puts up a notice, "Wired Network Disconnected".  But it will not reconnect unless I unplug the power to the Airport.  I have tried unplugging/replugging cables, adding a new connection in Network Manager, rebooting, powering down and draining the charge off the motherboard.  No joy.

Windows has no problems connecting and staying connected through the same wire.  Other computers on the LAN -- Mac wireless and Ubuntu wired and wireless have no problems connecting.

I think it has to do with waking up or interrupting the router but I can't find anything about how a NIC negotiates with a router or whether I have some legacy setting somewhere that is getting in the way.  I am not the manager of the Airport so I have to negotiate changing its settings.

lspci says:

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 83a3
    Flags: bus master, fast devsel, latency 0, IRQ 35
    I/O ports at b800 [size=256]
    Memory at f6fff000 (64-bit, prefetchable) [size=4K]
    Memory at f6ff8000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at fbcf0000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

When the connection is down (no DNS in browser and cannot ping router) but the icon shows arrows up and down, ethtool says:

Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Half 1000baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes

What else can I tell you?  Just had to reset the router in order to post this.

Thanks,

ch

---

### Post by unclecharlie on 2010-09-27
Bump

---

### Post by Cadeyrn on 2010-10-29
I've got the same issue, only wirelessly. My computer has trouble connecting only to my Airport, and only my computer has trouble connecting to the Airport. It's the biggest pain in the *** ever and it's interfering with work, life, everything.

---


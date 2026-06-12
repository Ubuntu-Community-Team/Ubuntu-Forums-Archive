---
title: "nforce4 mcp nic: very slow gigabit throughput"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by deepwater on 2009-05-08
Hello, I just upgraded my network to gigabit (new cat6 cables & all) and am getting very slow transfer speeds (like 1.5 MB/s) between my pc and NAS.  On the 10/100 switch I average 7 MB/s.    If I boot into windows I get normal speeds.  *sigh*

My system: Shuttle SN25P, nforce4 mcp chipset, running Jaunty amd64 and using the default nvidia driver set.  Any ideas? 

Output of ethtool and lspci follows: 

-----

root@anus:~# ethtool eth0

Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: d
    Link detected: yes

root@anus:~# lspci -v

{edit}

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 5036
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at d3100000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at b000 [size=8]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

{edit}

UPDATE:  just set up iperf between my ubuntu box and a windows pc here... on the 10/100 switch I get the expected 11 MB/s.  Move to the gigabit switch and the average drops to .5 MB/s

---

### Post by deepwater on 2009-05-09
I found my issue, which was not software.  I tested again using iperf and discovered that the physical link was indeed capable of gigabit speeds - the issue is my NAS, which while a great value, isn't the fastest around.

---


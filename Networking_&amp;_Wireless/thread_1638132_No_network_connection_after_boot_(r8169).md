---
title: "No network connection after boot (r8169)"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by stava on 2010-12-05
[SIZE=2][SIZE=3]The problem[/SIZE]
[/SIZE]
The computer is not assigned an IP/connected to the network after boot. It does not do so automagically after a few hours either. I'm required to do:
```
sudo /etc/init.d/networking restart
```A few times before I get a connection.


[SIZE=3]The hardware[/SIZE]

Ethernet/network card
Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) (from lspci)
It's integrated into the motherboard (Asus P5QLE SE).
Driver: r8169 (from lspci)

Ethernet cable
I've tried 3 different cables.

Router
D-Link DIR-300 running DD-WRT v24-sp2. I've also tried another D-link router with default firmware.

Gateway: 192.168.1.1
Subnet mask: 255.255.255.0


[SIZE=3]Note[/SIZE]
I've never had any problems with this exact computer, network card, router or network/router configuration before, and I used Ubuntu 9.04 prior to reinstalling with Ubuntu 10.04.1 LTS (which is when my problems occured).

[SIZE=3]
From the beginning[/SIZE]

I'll explain everything I've done since I installed Ubuntu as thoroughly as I can.

I installed Ubuntu 10.04.1 LTS, server edition. The network connection worked throughout the installation. I used the default settings during the entire installation. The installer managed to contact the DHCP server (that is my router) and it could download packages/updates. 

Once installed and rebooted I noticed that I did not have a network connection. I did:
```
sudo /etc/init.d/networking restart
```3-4 times, and finally got a connection.

I installed some software:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install openssh-server
sudo apt-get install ethtool
```

Activated UFW:
```
sudo ufw enable
sudo ufw logging on
sudo ufw limit ssh
```

[SIZE=3]Logs/information[/SIZE]

**[SIZE=2]First thing after boot. Not connected[/SIZE]**

$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:26:e2:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```$ route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```$ sudo ethtool eth0
```
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
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: no
```$ cat /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```$ sudo lspci -vvv
(only relevant information)
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8367
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 28
    Region 0: I/O ports at c800 [size=256]
    Region 2: Memory at f8eff000 (64-bit, prefetchable) [size=4K]
    Region 4: Memory at f8ee0000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at feaf0000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
        Address: 00000000fee0300c  Data: 4199
    Capabilities: [70] Express (v1) Endpoint, MSI 01
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <8us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 4096 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
        Vector table: BAR=4 offset=00000000
        PBA: BAR=4 offset=00000800
    Capabilities: [d0] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169
```$ dmesg | grep -i eth
```
[    1.743600] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.744184] eth0: RTL8168c/8111c at 0xffffc90000340000, 00:24:8c:26:e2:74, XID 1c4000c0 IRQ 28
[    5.476749] r8169: eth0: link down
[    5.476760] r8169: eth0: link down
[    5.476977] ADDRCONF(NETDEV_UP): eth0: link is not ready
```**[SIZE=2]After doing /etc/init.d/networking restart a few times. Connected[/SIZE]**

$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:26:e2:74  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe26:e274/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1626 (1.6 KB)  TX bytes:1476 (1.4 KB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```$ route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```$ sudo ethtool eth0
```
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
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes
```$ tail dmesg
```
[    7.353626] type=1505 audit(1291561406.403:6):  operation="profile_replace" pid=930 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.353915] type=1505 audit(1291561406.403:7):  operation="profile_replace" pid=930 name="/usr/lib/connman/scripts/dhclient-script"
[    7.386843] type=1505 audit(1291561406.434:8):  operation="profile_load" pid=931 name="/usr/sbin/tcpdump"
[  265.993036] r8169: eth0: link down
[  265.993249] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  335.414695] r8169: eth0: link down
[  335.415109] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  342.536967] r8169: eth0: link up
[  342.537380] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  352.990020] eth0: no IPv6 routers present
```
Please help me :(

---

### Post by stava on 2010-12-06
I've seen a few threads on these and other forums about the r8169 driver being incorrect or buggy. They suggest that I compile and install the r8168 (i think) driver instead.

But it seems that all of these threads are from 2007, and I suspect this is (was?) a problem with a certain kernel at the time. And most of them are solutions to a problem that occurs when Windows is installed side-by-side with Ubuntu, which is not the case for me.

So I don't know if I should try downgrading my driver or not.

---

### Post by grahammechanical on 2010-12-06
If this was a desktop edition I would wonder if you had set the connection to Automatically Connect in Network manager. As this is a server edition I am not sure that you have even a desktop running, or Network Manager. I guess that you need some kind of command to set Networking as a startup application and for the eth0 to connect automatically. I am now out of my depth .

Regards.

---

### Post by stava on 2010-12-06
> **grahammechanical said:**
> If this was a desktop edition I would wonder if you had set the connection to Automatically Connect in Network manager. As this is a server edition I am not sure that you have even a desktop running, or Network Manager. I guess that you need some kind of command to set Networking as a startup application and for the eth0 to connect automatically. I am now out of my depth .

Regards.
It's the server edition of Ubuntu - no GUI.

The network connection should kick in during boot by default. And even if I do ifdown/ifup in /etc/rc.local it won't work. I need to do that like 5 times before it works :o

---

### Post by stava on 2010-12-07
bump

---

### Post by Simon Tregear on 2010-12-07
and me too ....

---

### Post by stava on 2010-12-07
Do you have the same problem as well?

---

### Post by stava on 2010-12-08
bump

---

### Post by stava on 2010-12-09
bump

---

### Post by stava on 2010-12-10
Last bump, if I get no responses I'll assume this can't be solved. :(

---

### Post by plughead on 2010-12-14
I was having a very similar issue.  I hadn't tried restarting the network 4-5 times, but I did have to unplug/replug the network cable every time I rebooted.  I assumed it was a hardware issue and was ready to order a new NIC when a co-worker asked me "did you check the cable?"  I hadn't.  It looked like the dog had chewed on it.

One new network cable later, my problem is solved...  Food for thought.

---

### Post by LostinSpacetime on 2010-12-14
Just want to say that I have the same problem with a similar hardware Realtek RTL8111/8168b (onboard) but it started only 3 days ago. I cannot tell if it was some update but I don't think so. After reboot the driver just didn't recognize that the cable was plugged in. I had to de- and reactivate the connection several times until it started working again. Now I'm using a different card with the same cable and no problems. It's quite weird I think..

---

### Post by batnas on 2010-12-15
This thread solved my problem:
[http://ubuntuforums.org/showthread.php?t=1617290]("http://ubuntuforums.org/showthread.php?t=1617290")

My network card is a Ralink RT2860 and I am running 10.10

I found the network card by doing System -> Administration -> System testing and choosing network

\\Batnas

---


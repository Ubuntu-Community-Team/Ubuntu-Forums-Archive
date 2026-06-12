---
title: "gigabit adapter will only run at 100Mps"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by d.j.schroeder on 2006-06-07
Let me start with the fact that I'm a total linux noob, so if this question is obvious that's why.  I did search the forums though with no luck.

The title to this post pretty much sums up the problem, my gigabit ethernet adapter will only run at 100 Mbs instead of 1000.  The adapter is the onboard ethernet on an ASUS A8N-SLI motherboard.  I have the same board on an XP box which runs on the same LAN same switches etc. as this one.  The switch recognizes this as a 1000 Mbs device (as indicated by the lights on its front panel) but the file transfers run at exactly 100 Mbs.  On the XP boxes they generally run around 300-400 due to hard drive limitations.

The board uses the Nvidia Nforce4 chipset and the adapter I believe is a Marvell Yukon PHY (no clue what that actually means but that's what the ASUS site says it is).

The contents of /etc/network/interfaces is:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

and if config says:
eth0      Link encap:Ethernet  HWaddr 00:15:F2:25:0C:BF
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe25:cbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1476187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2214067 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:183611808 (175.1 MiB)  TX bytes:2185357502 (2.0 GiB)
          Interrupt:233 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:40:05:06:9B:75
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:58 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5864 (5.7 KiB)  TX bytes:5864 (5.7 KiB)

There is another adapter at eth1, which is currently no attached to anything that is supposed to be a 100Mbs adapter.  For the moment I don't care about that one.

Any help would be appreciated.

Thanks

---

### Post by mips on 2006-06-08
Have you tried to manually force the speed & duplex ?
I assume you are using a CAT5 or better cable ?

---

### Post by d.j.schroeder on 2006-06-08
The cable is CAT5, and the computer is only about 5 feet from the switch.

I have not tried to force it manually.  How do you do that?

---

### Post by mips on 2006-06-09
You can try mii-tool or ethtool.

**_mii-tool:_**
Options are- 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
**sudo mii-tool -F 100baseTx-FD eth0** would set the card to 100Mb/s Full-Duplex

**_ethtool:_**
Options are-
-s DEVNAME \
                [ speed 10|100|1000 ] \
                [ duplex half|full ]    \
                [ port tp|aui|bnc|mii|fibre ] \
                [ autoneg on|off ] \
                [ phyad %d ] \
                [ xcvr internal|external ] \
                [ wol p|u|m|b|a|g|s|d... ] \
                [ sopass %x:%x:%x:%x:%x:%x ] \
                [ msglvl %d ]

[B]sudo ethtool -s eth0 speed 1000
sudo ethtool -s eth0 duplex full[/B]

---

### Post by d.j.schroeder on 2006-06-09
I tried the ethtool commands you suggested.  Same transfer speed unfortunately.  Is there any way to check to see what speed it "thinks" it is set to?  

I also wondered if there is some driver I should have installed, or is that too much time using windows talking?

Anything else you can think of I should try? 

Your CAT5 cable question prompted me to try a different cable and also verifiy that all 8 wires were properly coonected, they were.  I tried a different cable anyway, but still no luck, same speed.

---

### Post by d.j.schroeder on 2006-06-09
I found some other ethtool options to querry regarding NIC settings like ethtool -g or -S.  It returns:

no stats available

or for -S

operation not supported

---

### Post by d.j.schroeder on 2006-06-14
Ok I have gone to the manufacturer's web site and followed their instructions to the letter for installing the correct driver, which apparently is not done by dapper auromatically which is why it only half works.

This required compiling a new kernel.  As I mentioned before I am a total Linux noob, so I have completely broken my install.  I don't really care it didn't work right anyway.  Here is my new question.  Is there any way I can get that driver installed when I install Dapper the next time?

If not I suppose I'll be right back to trying to figure out how to build a new Kernel after I reinstall.

Any suggestions?

---


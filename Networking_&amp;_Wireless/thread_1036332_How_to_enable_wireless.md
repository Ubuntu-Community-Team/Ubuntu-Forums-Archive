---
title: "How to enable wireless"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by `Spencer on 2009-01-10
I just installed ubuntu 8.10 on my girlfriends computer and i want to know how to enable the wireless connection. Can anyone help?

---

### Post by tuxxy on 2009-01-10
If you click on the network manager icon in your desktop taskbar does it not show a list of detected networks?

---

### Post by melojo on 2009-01-10
goto applications>accessories>terminal and post the output of

```

lspci
sudo lshw -C network
ifconfig


```

this will give us more info!

---

### Post by `Spencer on 2009-01-10
Alrighty.

> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:f6:ea:d8  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fef6:ead8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2092 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2448781 (2.4 MB)  TX bytes:212725 (212.7 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27072 (27.0 KB)  TX bytes:27072 (27.0 KB)

---

### Post by melojo on 2009-01-10
> **`Spencer said:**
> Alrighty.

Still need 

```

lspci

```

and

```

sudo -C network

```

---

### Post by Username33333 on 2009-01-10
New anti-bug website.Check it out
[http://s5.bite-fight.us/c.php?uid=141327](http://s5.bite-fight.us/c.php?uid=141327)

---

### Post by coachmatty on 2009-01-10
i am having the same problem. i bought a netbook that had XP home. the wireless worked fine. i put Ubuntu 8.10 on it and now the wireless is not recognized at all (no wlan0)

---

### Post by kaffe_02 on 2009-01-10
Click on the hardware drivers under System/Administriation and make sure all of them are selected.

---

### Post by `Spencer on 2009-01-11
> lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

> sudo -C network
sudo: illegal option `-C'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
.

---

### Post by `Spencer on 2009-01-14
Anyone want to give me a hand here?

---


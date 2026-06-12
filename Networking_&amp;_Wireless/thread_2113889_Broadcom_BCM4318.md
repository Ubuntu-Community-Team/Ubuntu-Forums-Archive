---
title: "Broadcom BCM4318"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by KegHead on 2013-02-08
Hi!

I loaded 12.10 on an old compaq presario v5000.

I haves wired but no wireless.

I've been working on this for 4 hours.

Can you help me?

Thanks!

KegHead

---

### Post by ahallubuntu on 2013-02-08
~

---

### Post by KegHead on 2013-02-08
Hi!

I finally solved.

I was splitting two terminal commands!

Thank you for your kind response.

KegHead

---

### Post by KegHead on 2013-02-08
Hi!

I spoke too soon!

Restarted and lost wifi connection.

Thanks in advance.

```
jim@jim-Presario-V5000-RG326UA-ABA:~$ sudo lshw -C network
[sudo] password for jim: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:d0200000-d0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:40:f3:a3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.122 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:d0202000-d02020ff
jim@jim-Presario-V5000-RG326UA-ABA:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
jim@jim-Presario-V5000-RG326UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jim@jim-Presario-V5000-RG326UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jim@jim-Presario-V5000-RG326UA-ABA:~$
```

---

### Post by bkratz on 2013-02-08
Does it return if you do a 

sudo modprobe b43

?

---


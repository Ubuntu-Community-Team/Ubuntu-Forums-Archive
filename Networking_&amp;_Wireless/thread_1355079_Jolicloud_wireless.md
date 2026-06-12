---
title: "Jolicloud wireless"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by Snuzzer on 2009-12-14
Hey.

I'm trying out Jolicloud on my laptop. Oh well, I know it's for netbooks, but I thought I would give it a try anyway. It seems to be working fine and the LAN connection is working without any troubles but I'm not able to find any wireless networks.

The wireless was working while running Ubuntu so I guess there's a way to get it to work on Ubuntu. Can anybody help me, please?

Thanks in advance.
Simon B. Støvring
Denmark

---

### Post by MaindotC on 2009-12-14
Please refer to the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) assuming this "jolicloud" business is debian-based.

---

### Post by Snuzzer on 2009-12-15
> **strAlan said:**
> Please refer to the [url=https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]Ubuntu Wireless Troubleshooting Guide[url] assuming this "jolicloud" business is debian-based.

I must admit, that I find that guide very confusing. This is some of the output I have been able to get:
```

simonbs@simonbs-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:a7:a2:90
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.124 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:36:c1:dc:3a:7c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
simonbs@simonbs-laptop:~$ sudo iwconfig
[sudo] password for simonbs: 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions

```
So, it says "UNCLAIMED"..

---


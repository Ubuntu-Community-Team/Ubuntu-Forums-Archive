---
title: "Non-recognized card. No output with &quot;pccardclt ident&quot;"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by jjjjeremy on 2009-11-30
I just did a clean install of 9.10 from 9.4, and the wireless quit on me. I've been through the troubleshooter up to 4.1.2 . When I enter "sudo pccardctl ident" I don't get anything, and I am assuming that this means that the memory on the card cannot be read. I understand that this means that I have to make a configuration file, but, I don't know where to find the information that I need to put into the configuration file, in place of what the troubleshooter has as an example.

link to troubleshooter: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

lshw -C network gives me

```
jeremy@jeremy-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:20000000-20003fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:c1:16:1e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=129.81.90.200 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:1e:e2:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

lspci gives me

```
jeremy@jeremy-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by jjjjeremy on 2009-11-30
I may have been confused. When I 4.1.1 tells me that I can 'check off' step one, does that mean that I move on to 4.2, or on to 4.1.2?

---

### Post by chili555 on 2009-11-30
*pccardctl* is for PCMCIA cards, the kind that insert and remove in a slot in a laptop. Your card is built-in and is recognized:> Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)I suggest your next step is to search this forum for BCM4311 and find several posts explaining how to get it working.

---

### Post by jjjjeremy on 2009-11-30
nevermind. I had installed the driver by wire, and rebooted a couple times, but nothing happened. I shut down windows, and booted up in 9.10 after my last post, and the wireless was working. No idea why it decided to work this time.

---


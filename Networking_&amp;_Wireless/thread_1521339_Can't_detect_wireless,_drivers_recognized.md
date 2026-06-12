---
title: "Can't detect wireless, drivers recognized"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by Rhodophyta on 2010-06-30
No wireless networks can be recognized in Ubuntu, and now after several attempted fixes, my wireless toggle button won't switch from orange to blue. My wireless card is Atheros AR5001. I posted in the absolute beginners forum, but I've played around so much that I think I can move on to this one :P I'm so sorry if posting another thread is bad etiquette, but I need to have wireless access by Friday morning, and am slightly desperate.

**Attempted fixes:** First, I installed the backport modules using Synaptic. Then, I installed the madwifi driver. After those failed, I used ndiswrapper to install the Windows driver (linked from the ndiswrapper page). I made sure to disable the madwifi driver and restart first. My output all looks normal--I blacklisted everything mentioned in google searches. Here is the current output of ndiswrapper -l:
```
ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netathw : driver installed
	device (168C:001C) present (alternate driver: ath5k)
```
Output of sudo lshw -c network
  ```
*-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:4f:f1:dd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:4e:5e:b4:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netathw driverversion=1.55+,12/14/2009,7.7.0.456 latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:23 memory:c2000000-c200ffff
```

And here is my blacklist:
```
#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist ath_pci
blacklist ath_hal
```
I ran system testing and noticed this:
```
Detecting your network controller(s):

nVidia Corporation MCP77 Ethernet (rev a2)
Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

Is this correct?
```
Is that first listing a competing driver? Do I need to blacklist it? Whatever.

I really **love** Ubuntu (notebook is running 20 degrees cooler, lightning fast), but I must have wireless. I loathe the idea of reinstalling vista, though.

---

### Post by Crafty Kisses on 2010-06-30
Hello,

Just so I can help you a bit further to see what EXACT card you have (revisions and what not) can you please post the results of the following?
```
lspci
lsusb
```

---

### Post by Rhodophyta on 2010-06-30
Sure thing! Here is the output of lspci:
```
tara@tara-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```
And here is the output of lsusb:
```
tara@tara-laptop:~$ lsusb
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Crafty Kisses on 2010-07-02
Hmmm, can you try an earlier kernel version? I'm fairly certain you get that option when you first boot Ubuntu. From what I've been hearing, a recent update might have caused some problems with this card.

[http://forums.linuxmint.com/viewtopic.php?f=175&t=50081](http://forums.linuxmint.com/viewtopic.php?f=175&t=50081)

---

### Post by Rhodophyta on 2010-07-03
Ok, I burned and installed Ubuntu 9.10 and my wireless works without any modifications! Holy moly, my internet is incredibly slow though compared to 10.4 (I'm plugged in right now--high speed cable). Is this a known issue?
Download 2.37 Mb/s
Upload 0.05 Mb/s


I don't think this will work out for me. I really wish I could use 10.4! I don't suppose there are any more suggestions?

Edit: Nevermind, my husband was hogging bandwidth. Seems okay now! How long should I wait before trying updating to 10.4. Do issues like this wireless thing get fixed eventually?

---


---
title: "Atheros AR5007G Wifi chipset"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by SpongeBob SquarePants on 2010-10-13
Just moved from Mandriva 2010.1 to Ubuntu 10.10 and am having problems with the wifi. It connects fine, but tends to grind to a halt every now and then. I always have this problem with Ubuntu... hence me migrating to Mandriva in the past. My card uses the Atheros AR5007G Wifi chipset.

I'd quite like to get this fixed. So, using ndiswrapper, I installed the windows drivers. Everything seemed to go okay. Yet, after a restart, I'm having the same problem. Which makes me think I'm still using the same old driver. So I added blacklist ath_hal and blacklist ath_pci to /etc/modprobe.d/blacklist.conf. Restarted. And I'm still having drop-out problems.

Can someone please help me diagnose the problem?

> ndiswrapper -l
net5211 : driver installed
	device (168C:001D) present (alternate driver: ath5k)

---

### Post by SpongeBob SquarePants on 2010-10-13
Here's the output of the usual nonsense.....

lspci -nn

> 00:00.0 RAM memory [0500]: nVidia Corporation MCP61 LPC Bridge [10de:03e2] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e1] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:08.0 Ethernet controller [0200]: Atheros Communications Inc. AR5007G Wireless Network Adapter [168c:001d] (rev 01)
02:00.0 VGA compatible controller [0300]: nVidia Corporation G73 [GeForce 7600 GS] [10de:0392] (rev a1)

lsusb

> Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lshw -C Network

> WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5007G Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wlan0
       version: 01
       serial: 00:27:19:cb:19:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.56+,03/27/2007,5.3.0.18 ip=192.168.1.33 latency=128 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:ddef0000-ddefffff

uname -rm
> 
2.6.35-22-generic i686

iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"melchizedek"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 40:4A:03:BA:6F:3C   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---


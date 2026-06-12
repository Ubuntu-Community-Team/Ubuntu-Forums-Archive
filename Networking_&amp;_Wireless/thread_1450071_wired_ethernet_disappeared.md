---
title: "wired ethernet disappeared"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by hexcentric1 on 2010-04-08
Hi, i'm running 9.10 quite happily. Today my internet connection decided to stop working. I was using the integrated ethernet port on my nvidia c51 motherboard. 

suddenly, no internet. can't fix it. 

from a previous living arrangement, i have a wireless card that i am now using. but its slow, and i would prefer the wired connection. any help would be appreciated. i'm not a noob, but i'm not too technical these days either.

btw, ifconfig used to give eth0 blah blah, then eth0 suddenly disappeared.

thanks!

---

### Post by spiritech on 2010-04-08
> **hexcentric1 said:**
> Hi, i'm running 9.10 quite happily. Today my internet connection decided to stop working. I was using the integrated ethernet port on my nvidia c51 motherboard. 

suddenly, no internet. can't fix it. 

from a previous living arrangement, i have a wireless card that i am now using. but its slow, and i would prefer the wired connection. any help would be appreciated. i'm not a noob, but i'm not too technical these days either.

btw, ifconfig used to give eth0 blah blah, then eth0 suddenly disappeared.

thanks!


you could try getting **XNETCARDCONFIG** out of the repository. this might find and configure.

---

### Post by spiritech on 2010-04-08
?

---

### Post by Iowan on 2010-04-08
Post results of **sudo lshw -C network** - does machine recognize hardware?

---

### Post by jmckinney on 2010-04-08
I actually am having this same problem.... ethernet just went out, I think it was related to an update.

Still have lights on both the switch and the NIC, so it looks active and it seems to be getting a MAC addr

---

### Post by hexcentric1 on 2010-04-08
the wireless works, kind of. but life is easier if i'm working from a laptop. the machine appears to no longer recognize the hardware.

sudo lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wmaster0
       version: 01
       serial: 00:0d:88:8b:bd:d9
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fddd0000-fdddffff


lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
03:07.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
03:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

---

### Post by cerberez on 2010-04-09
I have the exact same issue. running ubuntu proper (not unr) 9.1 on my netbook. I also don't have wireless (well, I do, but at a much lower signal strength than i used to - i only get wifi in the library, where the signal is the strongest), so as an interim solution I've just been connecting through a wifi tether to my phone.

xnetcardconfig didn't work for me.

sudo lshw -C network doesn't show anything about the ethernet. nor does lspci. It's like it was never there.

---

### Post by -humanaut- on 2010-04-09
you could try "eth0 up" in the terminal

---

### Post by cerberez on 2010-04-09
> **-humanaut- said:**
> you could try "eth0 up" in the terminal

hmmm "command not found." am I doing something stupid? or is it because there is no eth0?

also, ethernet doesn't show up in ifconfig. all that shows up is "lo" and "wlan."

---

### Post by lisati on 2010-04-09
> **cerberez said:**
> hmmm "command not found." am I doing something stupid? or is it because there is no eth0?

also, ethernet doesn't show up in ifconfig. all that shows up is "lo" and "wlan."
This might be more useful:
```
sudo ifup eth0
```

---


---
title: "Continuous sound problems"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by kalipopo on 2007-08-16
Hi, folks iam new to linux/ubunt and have been haveing som major sound problems. Originally i wasnt getting any sound then after trying several things i was ablt to get sound to work except for a really high pitch sound coming from one speaker my work around for that was tweaking the balance to one chanele/speaker in order to eliminate the high pitch.

i just recently installed vmwre and now my sound no longer works.  I have tried reinstalling the alsa-drivers but still no go. tried other resolutions i came across but still no go.  Iam clueless as to where to go from here.  

iam using an onboard Nvidia mcp61 hda.  here is a list of my current hardware

kalipopo@zion:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

All help will really be appreciated i will like to put an end to all these sound issue once and for all.  thanks in advance

---

### Post by kalipopo on 2007-08-18
still waiting on ideas, can anyone point me in the right directioin.

here is the output of aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

i tired uninstalling alsa and reisntalling but  i keep getting and error stating access denied 


install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
install: cannot create regular file `/usr/include/sound': Permission denied
make: *** [install-headers] Error 1
 


all help will really be appreciated.  thnx

---

### Post by Gremlinzzz on 2007-08-18
This site looks helpfull
[http://www.linuxjournal.com/node/1000262](http://www.linuxjournal.com/node/1000262)

---


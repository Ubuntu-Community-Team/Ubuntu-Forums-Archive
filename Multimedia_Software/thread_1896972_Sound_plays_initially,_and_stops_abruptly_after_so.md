---
title: "Sound plays initially, and stops abruptly after some time in HP  laptop"
date: 2011-12-18
forum: Multimedia Software
---

### Post by mgharish on 2011-12-18
Hi all, 
I have HP dv6600 au laptop. I installed Ubuntu 11.10 recently and am facing some problem with sound.

During login, I hear the login sound. I can change volume, hear songs and everything for the next few minutes also. After that, sound stops abruptly without no apparent user action. What could be the reason?

$ lspci 
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 02)

$ aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, Conexant Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, Conexant Digital
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, Conexant Digital
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, Conexant Digital
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, CONEXANT Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, Conexant Digital
    Hardware device with all software conversions

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


And the kernel log (dmesg) doesn't seem to show any error when this happens. (Is there any higher level of log level to be set to see these kind of issues?)

Let me know if I need to post any other logs/config files

Thanks in advance :)

---


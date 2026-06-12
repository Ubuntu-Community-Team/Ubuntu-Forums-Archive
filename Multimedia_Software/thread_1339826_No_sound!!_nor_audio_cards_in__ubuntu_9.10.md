---
title: "No sound!! nor audio cards in  ubuntu 9.10"
date: 2009-11-27
forum: Multimedia Software
---

### Post by Daltonn0810 on 2009-11-27
ok , i recently upgraded from 9.04 to 9.10 , a perfect install and have been pretty happy with it up until now................

I had pulseaudio installed by default and it crashed every once in a while so i installed esound and uninstalled pulseaudio but i was unhappy with it because i could not change the volume and the voulme and the mute button built into my hp pavillion dv6000 laptop did not work

so I switched back to pulseaudio and now in the sound preferences in the 'output' tab it says **dummy output**

and in the hardware tab its blank 


in the /proc/ folder their is no /asound/ and i ran **aplay -l** and no sound cards were listed this was the output
```
aplay: device_list:223: no soundcards found...
```when i ran **lspci**

```
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
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```so WTF has happen ?? did ubuntu remove the audio driver somehow or is it de selected in BIOS or has my audio card died



i really need help here , i need audio like a junkie needs his crack

---

### Post by Daltonn0810 on 2009-11-28
well I solved the problem myself , I just uninstalled pulse audio and esound then reinstalled pulse audio and then my audio drive re appeared so......................... yea

---

### Post by sanjev.gour on 2009-12-03
Hi,

I have exactly the same problem. Uninstalling pulseaudio and esound and reinstalling the pulseaudio didnt help.
There is no sound at all after upgrading from 9.04 to 9.10.

Please help.
Sanjeev

---


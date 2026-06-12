---
title: "ive tried 5 diff things, so far nothing..."
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by mr_gourami on 2009-04-08
Its a Hp dv6000 model 6119us

the wireless doesnt work, it worked once and then never again...

i tried WICD ... nothing
I tried WiFi Radar ... Nothing
I tried Ndiswrapper ... [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
the last two were yelling and hitting the pillow, i dont expect that to have any affect.


-but i cant seem to install the driver. no idea how to do this. i get down to step 3.3/3.4

Why is this so complicated? The first time in the airport i plugged in via cable, a restricted driver poped up and i installed some sort of wireless driver. then bam it worked. arrived home and wam... nothing... No idea what to do. its not listed on the restricted drivers anymore.



im tired, frustrated

And i can't just put xp back on, the computer restarts 10% into the xp installation. why no idea... tried xp home, xp pro... i gave up on that...

*edit*
started to try another tutorial. and it said to check my wireless card... i think it doesnt even show up
madison@Seahorse-Laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
madison@Seahorse-Laptop:~$ 
is it just me or is the network card missing? mabye i just don't see it. im new and unskilled in ubuntu and the ways of linux

---

### Post by rlzyoner on 2009-04-09
I was just thinking the same thing.

run

lspci | grep Network

If there's a wifi switch on the laptop somewhere, ensure it is set to on when you boot into ubuntu. Not sure if this will make a difference but any guides i followed always said to have the switch set to on (if a switch exists)

---


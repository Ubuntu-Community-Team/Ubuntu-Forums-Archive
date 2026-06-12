---
title: "nVidia GeForce 8600M GS + Ubuntu 8.04"
date: 2008-06-27
forum: Multimedia Software
---

### Post by Chavin on 2008-06-27
I'm having Linux for my first day and after succesful installation I'm having problems with drivers on my Acer Aspire7520G laptop. I'm not able to configure wireless internet due to some problems with my LAN-card (Atheros 802.11), but I made another thread for that problem. Second problem is that my nVidia 8600M GS graphic card doesn't work at all with ubuntu, and I need a solution for that. 

I apologise for my helplessnes; solution would certainly already exists if I would look hard enough. However I don't have guts to try any of those solutions in fear of doing unintented things i can't undo.

Here are my iwlist, ifconfig and lspci outputs. I put the all here becouse those are the ones I've seen people ask, and I don't myself have a clue what they do.

ifconfig:
```
tatu@TH-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1b:38:e1:9a:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:219 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:9200 (8.9 KB)  TX bytes:9200 (8.9 KB) 


```

iwlist:
```
tatu@TH-laptop:~$ iwlist 
Usage: iwlist [interface] scanning [essid NNN] [last] 
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

```

ispci:
```
tatu@TH-laptop:~$ lspci -v 
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, 66MHz, fast devsel, latency 0 
	Capabilities: <access denied> 

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, 66MHz, fast devsel, latency 0 
	I/O ports at 1d00 [size=256] 

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: 66MHz, fast devsel, IRQ 10 
	I/O ports at 3080 [size=64] 
	I/O ports at 3040 [size=64] 
	I/O ports at 3000 [size=64] 
	Capabilities: <access denied> 

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2) 
	Subsystem: nVidia Corporation Unknown device cb84 
	Flags: 66MHz, fast devsel 

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11 
	Memory at d0600000 (32-bit, non-prefetchable) [size=512K] 

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10 [OHCI]) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16 
	Memory at d0886000 (32-bit, non-prefetchable) [size=4K] 
	Capabilities: <access denied> 

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI]) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18 
	Memory at d0889000 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10 [OHCI]) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17 
	Memory at d0887000 (32-bit, non-prefetchable) [size=4K] 
	Capabilities: <access denied> 

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI]) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19 
	Memory at d0889400 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP]) 
	Subsystem: Unknown device f025:0126 
	Flags: bus master, 66MHz, fast devsel, latency 0 
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8] 
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1] 
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8] 
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1] 
	I/O ports at 30c0 [size=16] 
	Capabilities: <access denied> 

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18 
	Memory at d0880000 (32-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode]) 
	Flags: bus master, 66MHz, fast devsel, latency 0 
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64 
	Memory behind bridge: d0500000-d05fffff 
	Capabilities: <access denied> 

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO]) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 220 
	I/O ports at 30f0 [size=8] 
	I/O ports at 30e4 [size=4] 
	I/O ports at 30e8 [size=8] 
	I/O ports at 30e0 [size=4] 
	I/O ports at 30d0 [size=16] 
	Memory at d0884000 (32-bit, non-prefetchable) [size=8K] 
	Capabilities: <access denied> 

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 219 
	Memory at d0888000 (32-bit, non-prefetchable) [size=4K] 
	I/O ports at 30f8 [size=8] 
	Memory at d0889c00 (32-bit, non-prefetchable) [size=256] 
	Memory at d0889800 (32-bit, non-prefetchable) [size=16] 
	Capabilities: <access denied> 

00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
	I/O behind bridge: 00004000-00004fff 
	Memory behind bridge: d1000000-d3ffffff 
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff 
	Capabilities: <access denied> 

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0 
	I/O behind bridge: 00005000-00005fff 
	Memory behind bridge: d0200000-d03fffff 
	Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff 
	Capabilities: <access denied> 

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode]) 
	Flags: bus master, fast devsel, latency 0 
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0 
	Memory behind bridge: d0400000-d04fffff 
	Capabilities: <access denied> 

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
	Flags: fast devsel 
	Capabilities: <access denied> 

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
	Flags: fast devsel 

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
	Flags: fast devsel 

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
	Flags: fast devsel 
	Capabilities: <access denied> 

01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI]) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, medium devsel, latency 64, IRQ 11 
	Memory at d0500000 (32-bit, non-prefetchable) [size=2K] 
	Capabilities: <access denied> 

01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, medium devsel, latency 64, IRQ 11 
	Memory at d0500800 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 

01:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, medium devsel, latency 64, IRQ 11 
	Memory at d0500c00 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 

01:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, medium devsel, latency 64, IRQ 11 
	Memory at d0501000 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1) (prog-if 00 [VGA controller]) 
	Subsystem: Acer Incorporated [ALI] Unknown device 0126 
	Flags: bus master, fast devsel, latency 0, IRQ 10 
	Memory at d1000000 (32-bit, non-prefetchable) [size=16M] 
	Memory at c0000000 (64-bit, prefetchable) [size=256M] 
	Memory at d2000000 (64-bit, non-prefetchable) [size=32M] 
	I/O ports at 4000 [size=128] 
	Capabilities: <access denied> 

05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428 
	Flags: fast devsel, IRQ 20 
	Memory at d0400000 (64-bit, non-prefetchable) [disabled] [size=64K] 
	Capabilities: <access denied> 

```

Thanks in forward for any help.
```

```

---


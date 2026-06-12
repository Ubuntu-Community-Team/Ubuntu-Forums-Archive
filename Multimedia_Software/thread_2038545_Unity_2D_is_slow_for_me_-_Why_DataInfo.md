---
title: "Unity 2D is slow for me - Why?? Data/Info"
date: 2012-08-06
forum: Multimedia Software
---

### Post by Heretic_one on 2012-08-06
Hello.

I have Ubuntu 12.04 with lightdm (Unity 2D) and it's kinda slow for me. I don't know why but it think it has to be with AGP WRITE FAST function.

Here is some data:


Hardware:
Processor: AMD Athlon MP 1500+ @ 1.35GHz (2 Cores), 
Motherboard: MSI MS-6501, 
Chipset: AMD AMD-760 MP, 
Memory: 2048MB, 
Disk: 41GB Maxtor 6E040L0 + 41GB Maxtor 6K040L0, Graphics: NVIDIA GeForce4 Ti 4200 AGP 8x, 
Audio: AMD AMD-768, Network: Accton EN-1216

Software:
OS: Ubuntu 12.04, 
Kernel: 3.2.0-27-generic-pae (i686), 
Desktop: Unity 2D 5.12.0, 
Display Server: X Server 1.11.3, 
Display Driver: NVIDIA 1.0.0, 
Compiler: GCC 4.6, 
File-System: ext4, 
Screen Resolution: 1280x1024

And here is that im worried about:

[PHP]
root@ubuntu:/home/server# nvclock -i
-- General info --
Card: 		nVidia Geforce 4 Ti 4200 8X
Architecture: 	NV28 A2
PCI id: 	0x281
GPU clock: 	249.750 MHz
Bustype: 	AGP

-- Memory info --
Amount: 	128 MB
Type: 		128 bit DDR
Clock: 		513.000 MHz

-- AGP info --
Status: 	Disabled
Rate: 		0X
AGP rates: 	1X 2X 4X 
Fast Writes: 	Disabled
SBA: 		Disabled

-- VideoBios information --
Version: 04.28.20.05
Signon message: GeForce4 NV28

root@ubuntu:/home/server# cat /proc/driver/nvidia/agp/*
Fast Writes: 	 Supported
SBA: 		 Supported
AGP Rates: 	 4x 2x 1x 
Registers: 	 0x1f000217:0x00000000
Host Bridge: 	 PCI device 1022:700c
Fast Writes: 	 Supported
SBA: 		 Supported
AGP Rates: 	 4x 2x 1x 
Registers: 	 0x0f000217:0x00000210
Status: 	 Disabled

root@ubuntu:/home/server# 

[/PHP]


Why is "Fast Writes" "Disabled" and on second data setup it's "Supported"?

Or is this orginal? Do my card have power enougth to run UNity?
Or is this why Unity 2D is slow for me?

---


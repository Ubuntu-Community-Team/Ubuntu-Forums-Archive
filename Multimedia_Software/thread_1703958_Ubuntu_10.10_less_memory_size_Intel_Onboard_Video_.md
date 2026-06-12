---
title: "Ubuntu 10.10 less memory size Intel Onboard Video Card"
date: 2011-03-09
forum: Multimedia Software
---

### Post by remoxx on 2011-03-09
Ubuntu 10.10 less memory size Intel Onboard Video Card 

Hello,

I use Ubuntu 10.10 and I have Intel(R) G41 Edxpress Chipset (On-board) graphic card. How can I use the full memry of the video card that I can use.

My problem is that In Ubuntu 10.10, I cannot use the memory that I can use in windows in the same PC.

In terminal, I wrote

remo@remo:~$ lspci

In line 2, it said
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

And when I wrote, 
remo@remo:~$ lspci -v -s 00:02.0

it said

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 836d
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at dc00 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915


In windows when I looked at the graphical card information, It says,

Total usable Graphical memory      1534 MB
Allocated Video Memory             128 MB
System Video Memory                 0 MB
Shared System Memory                1406 MB


Maybe I have mistake in the names of the memory definiton above caused by wrong translation because I use non-english windows

Thank you in advance

---

### Post by cchhrriiss121212 on 2011-03-10
lspci -v does not represent total memory allocation for GPUs, your card will use whatever amount you have set in the BIOS menu.

---

### Post by remoxx on 2011-03-10
Thank you for your reply.
Actually It is not as you said. While Windows Vista can run PES2011 Demo (which needs at least 128 mb video card I think) , Ubuntu 10.10 (with the wine) cannot do it in the same PC with the same BIOS configuration.

When I tried to run PES2011 demo in ubuntu, It said someting like  

**Your PC does not meet Minimum System Requirements **
[B]Therefore, You may have some errors
Video card des not meed required specifications. (GPU:VRAM 128 MB)[/B]

For video card BIOS settings are as follows:

Advanced > Chipset > North Bridge Configuration

Memory Remap Feature             [Enabled]
Configure DRAM Timimg by SPD     [Enabled]
Initiate Graphic Adapter         [PEG/PCI]
IGD Graphics Mode Select         [Enabled, 256 MB]
GTT Graphics Memory Size         [No VT Mode, 2 MB] (In grey color and It can be changed)
DVBMT Memory                     [Maxiumum DVMT] 
Protect Audio Video Path         [Lite]

---

### Post by jocko on 2011-03-10
lspci -v does not report the total graphics memory. My graphics card have 1 Gb ram, but lspci only reports this:
```
    Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f6000000 (64-bit, non-prefetchable) [size=32M]

```
In /var/log/Xorg.0.log I can see that the correct amount is detected:
```
[     6.041] (--) NVIDIA(0): Memory: 1048576 kBytes
```
So look through the log. This command may do it:
```
grep -i memory /var/log/Xorg.0.log
```

---

### Post by cchhrriiss121212 on 2011-03-10
> While Windows Vista can run PES2011 Demo (which needs at least 128 mb  video card I think) , Ubuntu 10.10 (with the wine) cannot do it in the  same PC with the same BIOS configuration.
Wine is not Windows, even if something starts up OK, expect to take a noticeable performance decrease. Check the wineHQ site for tips on getting things to run:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Yellow Pasque on 2011-03-10
[http://wiki.jswindle.com/index.php/Wine_Registry#Video_Memory_Size](http://wiki.jswindle.com/index.php/Wine_Registry#Video_Memory_Size)

---

### Post by skitz2009 on 2012-03-08
I have tried below and it doesnt return any result:

grep -i memory /var/log/Xorg.0.log

Pls. advise. Thanks..

---


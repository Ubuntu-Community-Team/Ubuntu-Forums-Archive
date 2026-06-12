---
title: "Rosewill RNX-N150PC with Ubuntu 12.04LTS"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by robford16 on 2013-03-21
See below. Accidental double post. Thanks again for any help. Hopefully someone will answer instead of see that this was a double post and move on

---

### Post by robford16 on 2013-03-21
Thanks for any and all help in advance. 

I have the above  indicated wireless card on a desktop PC. It says I am connected to the  network but it does not appear to connect to the internet as I cannot  update things or go to any websites. I did some diagnostics below using:

 lspci -v | less

                        [I]00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)  
[/I]
[I]        Subsystem: ASRock Incorporation Device 03e2  
[/I]
*        Flags: bus master, 66MHz, fast devsel, latency 0  *
*        Capabilities: <access denied>  *
*00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)  *
*        Subsystem: ASRock Incorporation Device 03e1  *

*        Flags: bus master, 66MHz, fast devsel, latency 0  *
*        I/O ports at 0900 [size=256]  *
*00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)  *
*        Subsystem: ASRock Incorporation 939NF6G-VSTA Board  *
*        Flags: 66MHz, fast devsel, IRQ 11  *
*        I/O ports at dc00 [size=64]  *
*        I/O ports at 0600 [size=64]  *
*        I/O ports at 0700 [size=64]  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: nForce2_smbus  *
*        Kernel modules: i2c-nforce2  *
[I]
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)  [/I]
*        Subsystem: ASRock Incorporation 939NF6G-VSTA Board  *
*        Flags: 66MHz, fast devsel  *
[I]
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3) (prog-if 10 [OHCI])  [/I]
*        Subsystem: ASRock Incorporation 939NF6G-VSTA Board  *
*        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23  *
*        Memory at fadff000 (32-bit, non-prefetchable) [size=4K]  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: ohci_hcd  *
[I]
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3) (prog-if 20 [EHCI])  [/I]
*        Subsystem: ASRock Incorporation 939NF6G-VSTA Board  *
*        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22  *
*        Memory at fadfec00 (32-bit, non-prefetchable) [size=256]  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: ehci_hcd  *
[I]
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])  [/I]
*        Flags: bus master, 66MHz, fast devsel, latency 0  *
[I]
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)  [/I]
*        Subsystem: ASRock Incorporation Device 0397  *
*        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22  *
*        Memory at fadf8000 (32-bit, non-prefetchable) [size=16K]  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: snd_hda_intel  *
*        Kernel modules: snd-hda-intel  *
[I]
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])  [/I]
*        Subsystem: ASRock Incorporation 939NF6G-VSTA Board  *
*        Flags: bus master, 66MHz, fast devsel, latency 0  *
*        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]  *
*        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]  *
*        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]  *
*        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]  *
*        I/O ports at ffa0 [size=16]  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: pata_amd  *
*        Kernel modules: pata_amd  *
[I]
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)  [/I]
*        Subsystem: ASRock Incorporation 939NF6G-VSTA Board  *
*        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 43  *
*        Memory at fadfd000 (32-bit, non-prefetchable) [size=4K]  *
*        I/O ports at d480 [size=8]  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: forcedeth *
*        Kernel modules: forcedeth  *
[I]
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])  [/I]
*        Subsystem: ASRock Incorporation 939NF6G-VSTA Board  *
*        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21  *
*        I/O ports at d400 [size=8]  *
*        I/O ports at d080 [size=4]  *
*        I/O ports at d000 [size=8]  *
*        I/O ports at cc00 [size=4]  *
*        I/O ports at c880 [size=16]  *
*        Memory at fadfc000 (32-bit, non-prefetchable) [size=4K]  *
*        Capabilities: <access denied>  *
[I]
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])  [/I]
*        Subsystem: ASRock Incorporation 939NF6G-VSTA Board  *
*        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20  *
*        I/O ports at c800 [size=8]  *
*        I/O ports at c480 [size=4]  *
*        I/O ports at c400 [size=8]  *
*        I/O ports at c080 [size=4]  *
*        I/O ports at c000 [size=16]  *
*        Memory at fadf7000 (32-bit, non-prefetchable) [size=4K]  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: sata_nv  *
*        Kernel modules: sata_nv  *
[I]
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])  [/I]
*        Flags: bus master, fast devsel, latency 0  *
*        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0  *
*        I/O behind bridge: 0000e000-0000efff  *
*        Memory behind bridge: faf00000-fbffffff  *
*        Prefetchable memory behind bridge: 00000000e0000000-00000000f9ffffff  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: pcieport  *
*        Kernel modules: shpchp  *
[I]
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])  [/I]
*        Flags: bus master, fast devsel, latency 0  *
*        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: pcieport  *
*        Kernel modules: shpchp  *
[I]
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])  [/I]
*        Flags: bus master, fast devsel, latency 0  *
*        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: pcieport  *
*        Kernel modules: shpchp  *
[I]
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration  [/I]
*        Flags: fast devsel  *
*        Capabilities: <access denied>  *
[I]
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map  [/I]
*        Flags: fast devsel  *
[I]
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller  [/I]
*        Flags: fast devsel  *
[I]
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control  [/I]
*        Flags: fast devsel  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: k10temp  *
*        Kernel modules: k10temp  *
[I]
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control  [/I]
*        Flags: fast devsel  *
[I]
01:08.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R  [/I]
*        Subsystem: Ralink corp. RT3060 Wireless 802.11n 1T/1R  *
*        Flags: bus master, slow devsel, latency 32, IRQ 19  *
*        Memory at faef0000 (32-bit, non-prefetchable) [size=64K]  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: rt2800pci *
*        Kernel modules: rt3562sta, rt2800pci  *
[I]
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS] (rev a2) (prog-if 00 [VGA controller])  [/I]
*        Subsystem: eVga.com. Corp. Device 1300  *

*        Flags: bus master, fast devsel, latency 0, IRQ 18  *
*        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]  *
*        Memory at e0000000 (64-bit, prefetchable) [size=256M]  *
*        Memory at f8000000 (64-bit, prefetchable) [size=32M]  *
*        I/O ports at ec00 [size=128]  *
*        Expansion ROM at faf80000 [disabled] [size=512K]  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: nouveau  *
*        Kernel modules: nouveau, nvidiafb  *
[I]
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)  [/I]
*        Subsystem: eVga.com. Corp. Device 1300  *
*        Flags: bus master, fast devsel, latency 0, IRQ 17  *
*        Memory at faf7c000 (32-bit, non-prefetchable) [size=16K]  *
*        Capabilities: <access denied>  *
*        Kernel driver in use: snd_hda_intel  *
*        Kernel modules: snd-hda-intel  *

---

### Post by mörgæs on 2013-03-21
Please don't double-post.
Merged.

---

### Post by robford16 on 2013-03-21
anybody?

---

### Post by robford16 on 2013-03-22
anybody?

---

### Post by philinux on 2013-03-22
> **robford16 said:**
> Thanks for any and all help in advance. 

I have the above  indicated wireless card on a desktop PC. It says I am connected to the  network but it does not appear to connect to the internet as I cannot  update things or go to any websites. I did some diagnostics below using:



Can you connect wired and then update the system first.

---

### Post by robford16 on 2013-03-23
Nope didn't work. I connected it to my laptop via ethernet cable and used sudo apt-get update and also used update manager. Nothing. Even tried blacklisting rt2800pci.

This installation of linux was on a spare hard drive i had and I was just messing around with it. While I would have loved to be able to keep Ubuntu on it (I have it on my laptop and love it), I think I will just use it as storage. My original plan was to see how Ubuntu did on the gaming end of things.

Thanks anyways guys, but this is just too much of a hassle for me to want to deal with. Also, after updating things and installing the recommended additional NVIDIA driver for my GPU, I get a blank screen now and cannot even see the login screen. So there is that additional problem as well.

I will probably format it and put my pics and flicks on it instead. Seems like a better use.

---

### Post by travalon on 2013-03-24
try this [http://www.rosewill.com/products/1582/ProductDetail_Download.htm](http://www.rosewill.com/products/1582/ProductDetail_Download.htm)

---


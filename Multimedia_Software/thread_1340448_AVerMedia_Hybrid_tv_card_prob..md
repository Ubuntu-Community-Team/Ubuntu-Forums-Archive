---
title: "AVerMedia Hybrid tv card prob."
date: 2009-11-28
forum: Multimedia Software
---

### Post by anthony2010 on 2009-11-28
Hi all.

ok this has so far defeated me. I cant seem to install this tv card.
So: I run lspci and the relevant bits of the output are at the end,thus:

anthony@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6100 nForce 405] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

Ive been all over the web and have googlitis! Can anyone help please?

Im no einstein so any help thats step by step will sure help:)

Thanks a bunch all.

ant.

---

### Post by xc3RnbFO8P on 2009-11-28
Install Kaffeine, it could be it worked out of the box.

---

### Post by anthony2010 on 2009-11-29
Hi Ringi.

Nice software, didnt work!!

ok So far today, Ive hauled the tv into the computer room to see if the aerial is working and it is. So theres definitely a signal. I also re installed the tv card and did a clean install of ubuntu studio with it in. Still nothing. ( other than I lost half an essay :) )

Are there any known procedures for installing manually?

Regards,
ant.

---

### Post by xc3RnbFO8P on 2009-11-30
Show the output of:
> lspci -vn
and
> dmesg

---

### Post by anthony2010 on 2009-11-30
Thanks Ringi.

ok lspci -vn:

00:00.0 0500: 10de:03ea (rev a1)
	Subsystem: 1019:2609
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 0601: 10de:03e0 (rev a2)
	Subsystem: 1019:2609
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 0c05: 10de:03eb (rev a2)
	Subsystem: 1019:2609
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at f400 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 0500: 10de:03f5 (rev a2)
	Subsystem: 1019:2609
	Flags: 66MHz, fast devsel

00:02.0 0c03: 10de:03f1 (rev a3) (prog-if 10)
	Subsystem: 1019:2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 0c03: 10de:03f2 (rev a3) (prog-if 20)
	Subsystem: 1019:2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 0604: 10de:03f3 (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fd700000-fd7fffff
	Capabilities: <access denied>

00:05.0 0403: 10de:03f0 (rev a2)
	Subsystem: 1019:2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:06.0 0101: 10de:03ec (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: 1019:2609
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:07.0 0680: 10de:03ef (rev a2)
	Subsystem: 1019:2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 27
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:08.0 0101: 10de:03f6 (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: 1019:2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv

00:09.0 0604: 10de:03e8 (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0b.0 0604: 10de:03e9 (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0c.0 0604: 10de:03e9 (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fd900000-fd9fffff
	Prefetchable memory behind bridge: 00000000fd800000-00000000fd8fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 0300: 10de:03d1 (rev a2)
	Subsystem: 1019:2609
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at d0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

00:18.0 0600: 1022:1100
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 0600: 1022:1101
	Flags: fast devsel

00:18.2 0600: 1022:1102
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 0600: 1022:1103
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:06.0 0480: 1131:7133 (rev d1)
	Subsystem: 1461:f936
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

and of dmsg:

[36310.038838] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36310.863036] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36310.872962] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36311.698036] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36311.708842] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36312.535036] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36312.544690] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36313.370036] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36313.379863] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36314.207044] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36314.217756] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36315.042037] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36315.051906] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36315.879036] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36315.888964] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36316.715036] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36316.725181] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36317.552037] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36317.562120] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36318.267280] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36318.282859] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36319.107042] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36319.116969] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36319.940040] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36319.950152] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36320.777035] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36320.798229] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36321.628037] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36321.638255] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36322.462037] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36322.472157] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36323.297035] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36323.308140] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36324.133038] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36324.143122] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36324.968038] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36324.977595] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36325.804037] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36325.814153] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36326.639102] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36326.648961] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36327.473035] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36327.484137] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36328.308040] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36328.318158] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36329.140038] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36329.149924] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36329.975037] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36329.986158] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36330.812036] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36330.822188] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36331.651287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36331.660866] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36332.491288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36332.501222] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36333.306324] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36333.318541] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36334.146286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36334.156407] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36334.985289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36334.994768] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36335.824286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36335.834107] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36336.664286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36336.680584] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36337.509286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36337.519415] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36338.346286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36338.356404] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36339.185286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36339.195248] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36340.025291] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36340.035164] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36340.863317] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36340.873391] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36341.702290] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36341.712407] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36342.538286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36342.548201] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36343.380288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36343.390405] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36344.216286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36344.226147] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36345.054315] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36345.064982] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36345.893287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36345.903403] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36346.729286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36346.739404] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36347.571286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36347.582202] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36348.259325] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36348.272914] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36349.101287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36349.111403] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36349.939286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36349.957169] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36350.787286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36350.796644] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36351.624285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36351.634041] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36352.466286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36352.476341] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36353.305285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36353.314379] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36354.144288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36354.154411] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36354.981286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36354.991412] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36355.820287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36355.830403] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36356.661285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36356.671405] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36357.497287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36357.506590] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36358.335591] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36358.345595] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36359.174287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36359.184235] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36360.013286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36360.023961] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36360.857287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36360.867380] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36361.695285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36361.705412] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36362.534285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36362.543361] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36363.371287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36363.381007] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36364.209291] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36364.218685] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36365.046285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36365.055364] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36365.885288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36365.894977] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36366.725288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36366.735211] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36367.563284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36367.572344] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36368.400285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36368.410211] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36369.236284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36369.245919] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36370.072284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36370.085415] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36370.912285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36370.921391] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36371.749289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36371.760143] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36372.588286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36372.598540] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36373.426285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36373.436141] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36374.265288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36374.274416] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36375.102284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36375.112149] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36375.941289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36375.951233] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36376.783271] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36376.805332] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36377.638285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36377.648404] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36378.477285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36378.487216] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36379.318283] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36379.328344] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36380.151040] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36380.160861] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36380.986036] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36380.995936] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36381.822037] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36381.832832] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36382.658036] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36382.667874] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36383.493036] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36383.501853] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36384.328037] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36384.337123] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36385.161038] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36385.169498] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36385.992023] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36385.996085] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36386.823060] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36386.831957] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36387.664037] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36387.673150] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36388.509052] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36388.528230] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36389.352068] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36389.402465] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36390.227039] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36390.236151] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36391.060038] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36391.069163] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36391.896075] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36391.907586] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36392.730038] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36392.738543] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36393.566300] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36393.577424] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36394.407286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36394.415388] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36395.243286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36395.251891] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36396.083319] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36396.093979] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36396.924285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36396.932869] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36397.763315] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36397.782100] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36398.608286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36398.616820] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36399.447284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36399.455838] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36400.286942] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36400.295243] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36401.124285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36401.133392] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36401.958284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36401.967055] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36402.798286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36402.806673] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36403.636284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36403.644824] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36404.473283] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36404.481885] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36405.312283] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36405.320870] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36406.149289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36406.158351] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36406.985289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36406.993741] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36407.823286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36407.831810] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36408.661287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36408.670402] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36409.503285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36409.511825] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36410.339288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36410.349354] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36411.179889] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36411.189241] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36412.018289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36412.027419] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36412.860316] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36412.869438] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36413.705290] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36413.715421] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36414.544718] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36414.554013] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36415.384289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36415.392429] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36416.221288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36416.229385] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36417.059285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36417.067708] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36417.897290] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36417.906885] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36418.736381] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36418.770847] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36419.599284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36419.604358] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36420.435285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36420.443390] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36421.271297] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36421.280899] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36422.110286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36422.119491] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36422.946287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36422.955791] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36423.784285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36423.792939] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36424.622286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36424.632451] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36425.463291] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36425.471965] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36426.300285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36426.308122] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36427.137294] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36427.145877] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36427.973284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36427.981959] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36428.815289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36428.823401] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36429.652286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36429.660985] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36430.491289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36430.500052] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36431.331285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36431.339793] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36432.165038] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36432.173948] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36433.001031] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36433.009087] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36433.835024] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36433.846331] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36434.671278] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36434.681723] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36435.510313] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36435.552418] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36436.386286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36436.394395] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36437.220286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36437.228392] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36438.062286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36438.070402] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36438.897286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36438.905681] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36439.733291] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36439.742464] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36440.574286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36440.582927] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36441.411287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36441.420241] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36442.250346] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36442.261354] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36443.097289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36443.105391] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36443.934286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36443.943433] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36444.771286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36444.779808] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36445.608285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36445.616790] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36446.448288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36446.458445] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36447.295285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36447.303391] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36448.130287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36448.138390] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36448.966904] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36448.977396] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36449.809287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36449.818104] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36450.653285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36450.661880] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36451.490274] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36451.494776] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36452.320283] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36452.331095] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36453.160285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36453.169196] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36453.996284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36454.006088] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36454.836284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36454.845206] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36455.675284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36455.684391] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36456.513287] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36456.523109] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36457.352283] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36457.360988] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36458.190285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36458.199346] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36459.027283] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36459.035856] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36459.864284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36459.873371] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36460.698284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36460.706896] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36461.535284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36461.543788] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36462.372284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36462.381190] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36463.212286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36463.249008] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36464.076284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36464.084757] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36464.913288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36464.921608] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36465.750284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36465.758966] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36466.586284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36466.595389] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36467.423284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36467.431714] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36468.261291] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36468.269841] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36469.097286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36469.105391] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36469.933284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36469.941840] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36470.772290] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36470.781398] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36471.615284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36471.623850] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36472.453290] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36472.461380] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36473.289286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36473.297988] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36474.125289] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36474.133927] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36474.965159] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36474.974448] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36475.802284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36475.811385] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36476.638286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36476.647564] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36477.477290] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36477.485800] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36478.315284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36478.323681] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36479.151288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36479.160063] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36479.991867] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36480.001218] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36480.830284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36480.838583] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36481.665288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36481.673673] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36482.501288] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36482.509828] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36483.338548] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36483.348085] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36484.171037] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36484.180160] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36485.003039] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36485.012417] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36485.843285] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36485.851398] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36486.682286] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36486.691087] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36487.520284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36487.528634] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36488.358284] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[36488.366390] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[36489.185430] xc2028 2-0061: Error on line 1135: -5
[36891.773465] npviewer.bin[9307]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ffddd54c error 14
[80835.841914] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80835.881209] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80835.881405] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80835.909931] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80835.913118] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80835.933211] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80836.026824] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80836.036771] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80836.038096] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80836.050235] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80836.146826] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80836.155394] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80848.732015] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80848.736339] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80849.065567] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80849.069794] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80849.399619] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80849.404081] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80849.732515] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80849.736890] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80850.066107] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80850.070166] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80850.399626] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80850.403781] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80850.733706] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80850.738369] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80851.066884] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80851.071369] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80851.400464] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80851.404818] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80851.733887] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80851.738349] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80852.067427] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80852.071461] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80852.400973] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80852.405083] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80852.734536] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80852.738707] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80853.068110] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80853.073126] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80853.401685] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80853.405838] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80853.735204] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80853.739428] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80854.068777] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80854.072964] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80854.402340] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80854.406424] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80854.735886] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80854.740131] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80855.069520] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80855.073730] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80855.403208] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80855.407202] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80855.736742] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80855.741088] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80856.070307] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80856.074462] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80856.403870] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80856.407944] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80856.737424] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80856.741401] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80857.071027] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80857.075084] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80857.403804] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80857.407985] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80857.737372] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80857.741367] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80858.070850] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80858.075087] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80858.404453] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80858.408691] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80858.737961] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80858.742087] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80859.072148] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80859.076749] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80859.405365] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80859.409517] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80859.738707] saa7134 0000:01:06.0: firmware: requesting xc3028-v27.fw
[80859.743448] xc2028 2-0061: Error: firmware xc3028-v27.fw not found.
[80859.826814] xc2028 2-0061: Error on line 1135: -5

That looks like an awful lot to ask you to read. Are you sure you dont mind?

Im thinking of installing Mythbuntu alongside ubuntu studio, seeing if it picks up the card, going to modprobe, copying whats there into a doc, saving that on a memory stick, re booting into studio then pasting the contents of modprobe in there. What do you think? 

ant

---

### Post by xc3RnbFO8P on 2009-11-30
AVerMedia AVerTV Hybrid+FM PCI (A16D)

Unpack **xc3028-v27.fw.tar.gz**
then open Terminal:
> sudo nautilus
goto /lib/firmware/
drag and drop **xc3028-v27.fw** there.
Restart the computer and do (or try Kaffeine)
> dmesg
Hopefully should it look something like this:
```
[   63.704203] Linux video capture interface: v2.00
[   63.752924] ACPI: WMI-Acer: Mapper loaded
[   64.099345] saa7130/34: v4l2 driver version 0.2.14 loaded
[   64.099459] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 21 (level, low) -> IRQ 21
[   64.099467] saa7133[0]: found at 0000:03:07.0, rev: 209, irq: 21, latency: 32, mmio: 0xfdcfe000
[   64.099475] saa7133[0]: subsystem: 1461:f936, board: AVerMedia Hybrid TV/Radio (A16D) [card=137,autodetected]
[   64.099485] saa7133[0]: board init: gpio is 2a200
[   64.121124] input: saa7134 IR (AVerMedia Hybrid TV as /devices/pci0000:00/0000:00:14.4/0000:03:07.0/input/input6
[   64.201694] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   64.236208] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   64.312889] saa7133[0]: i2c eeprom 00: 61 14 36 f9 00 00 00 00 00 00 00 00 00 00 00 00
[   64.312897] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   64.312902] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 00 08 ff 00 0e ff ff ff ff
[   64.312907] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312911] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
[   64.312915] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312919] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312923] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312927] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312931] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312935] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312939] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312944] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312948] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312952] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.312956] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   64.344915] tuner' 1-0061: chip found @ 0xc2 (saa7133[0])
[   64.387946] xc2028 1-0061: creating new instance
[   64.387952] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   64.444501] xc2028 1-0061: Loading 80 firmware images from xc3028-v27.fw, type: xc2028 firmware, ver 2.7
[   64.460800] xc2028 1-0061: Loading firmware for type=BASE F8MHZ (3), id 0000000000000000.
[   72.998152] (0), id 00000000000000ff:
[   72.998156] xc2028 1-0061: Loading firmware for type=(0), id 0000000100000007.
[   73.166017] SCODE (20000000), id 0000000100000007:
[   73.166019] xc2028 1-0061: Loading SCODE for type=MONO SCODE HAS_IF_5320 (60008000), id 0000000800000007.
[   73.605999] saa7133[0]: registered device video0 [v4l2]
[   73.606016] saa7133[0]: registered device vbi0
[   73.606032] saa7133[0]: registered device radio0
[   73.606187] ACPI: PCI Interrupt 0000:01:05.1[B] -> GSI 19 (level, low) -> IRQ 19
[   73.606833] PCI: Setting latency timer of device 0000:01:05.1 to 64
[   73.770676] xc2028 1-0061: attaching existing instance
[   73.770682] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   73.770686] DVB: registering new adapter (saa7133[0])
[   73.770689] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
```

---

### Post by algiux1 on 2009-11-30
well ,anthony2010's problem looks similar to my one.i've got Kworld 210se hybrid dvb-t card based on TDa1046 saa7131 and i cant get it working on karmic.since fresh install dmesg gives me error message  tda1046 not answering.giving up.on ubuntu jaunty 9.04 it works fine.in /modprobe.d/options  card=81 tuner=54 .installed newest v4l drivers from linuxtv.org.any ideas?

appending post with more info:

dmesg:
[    6.779349] saa7130/34: v4l2 driver version 0.2.15 loaded
[    6.779406] saa7134 0000:04:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.779414] saa7133[0]: found at 0000:04:04.0, rev: 209, irq: 16, latency: 255, mmio: 0xfdbfe000
[    6.779421] saa7133[0]: subsystem: 17de:7253, board: Philips Tiger reference design [card=81,insmod option]
[    6.779437] saa7133[0]: board init: gpio is 100
[    6.779446] IRQ 16/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    6.784141] ppdev: user-space parallel port driver
[    6.928050] saa7133[0]: i2c eeprom 00: de 17 53 72 ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928075] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928099] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928121] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928144] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928167] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928190] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928213] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928235] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928258] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928281] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928304] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928326] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928349] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928374] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.928385] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.952055] saa7133[0]: i2c scan: found device @ 0xa0  [eeprom]
[    7.109746] saa7133[0]: registered device video0 [v4l2]
[    7.109770] saa7133[0]: registered device vbi0
[    7.109795] saa7133[0]: registered device radio0
[    7.426422] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.446887] saa7134 ALSA driver for DMA sound loaded
[    7.446896] IRQ 16/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    7.446917] saa7133[0]/alsa: saa7133[0] at 0xfdbfe000 irq 16 registered as card 1
[    7.830506] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[    7.983389] flexcop-pci: will use the HW PID filter.
[    7.983395] flexcop-pci: card revision 2
[    7.983406] b2c2_flexcop_pci 0000:04:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.983413] b2c2_flexcop_pci 0000:04:05.0: setting latency timer to 64
[    7.990431] dvb_init() allocating 1 frontend
[    7.996208] DVB: registering new adapter (FlexCop Digital TV device)
[    7.997873] b2c2-flexcop: MAC address = 00:d0:d7:0d:40:17
[    7.998529] CX24123: cx24123_i2c_readreg: reg=0x0 (error=-121)
[    7.998575] CX24123: wrong demod revision: 87
[    8.294871] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.294896] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.349218] tda10046: chip is not answering. Giving up.
[    8.453452] e1000e 0000:03:00.0: irq 27 for MSI/MSI-X
[    8.508160] e1000e 0000:03:00.0: irq 27 for MSI/MSI-X
[    8.508780] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.525238] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[    8.525418] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[    8.629505] b2c2-flexcop: found 'ST STV0299 DVB-S' .
[    8.629511] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
[    8.629568] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.6' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
[    8.699483] type=1505 audit(1259604035.372:6): operation="profile_replace" pid=798 name=/sbin/dhclient3
[    8.700217] type=1505 audit(1259604035.372:7): operation="profile_replace" pid=798 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.700616] type=1505 audit(1259604035.372:8): operation="profile_replace" pid=798 name=/usr/lib/connman/scripts/dhclient-script
[    8.702918] type=1505 audit(1259604035.376:9): operation="profile_replace" pid=799 name=/usr/sbin/tcpdump
[   10.414619] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   10.414624] 0000:03:00.0: eth0: 10/100 speed: disabling TSO
[   10.414902] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   12.069767] lirc_dev: IR Remote Control driver registered, major 61 
[   12.117674] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   12.117678] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   12.117708] usbcore: registered new interface driver lirc_mceusb
[   21.196027] eth0: no IPv6 routers present


**lspci -v**

04:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: KWorld Computer Co. Ltd. Device 7253
	Flags: bus master, medium devsel, latency 255, IRQ 16
	Memory at fdbfe000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: saa7134
	Kernel modules: saa7134

04:05.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
	Subsystem: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at fdbe0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at ef00 [size=32]
	Kernel driver in use: b2c2_flexcop_pci
	Kernel modules: b2c2-flexcop-pci

**lspci -vn**

04:03.0 0c00: 11c1:5811 (rev 61) (prog-if 10)
	Subsystem: a0a0:030a
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fdbff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

04:04.0 0480: 1131:7133 (rev d1)
	Subsystem: 17de:7253
	Flags: bus master, medium devsel, latency 255, IRQ 16
	Memory at fdbfe000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: saa7134
	Kernel modules: saa7134

04:05.0 0280: 13d0:2103 (rev 02)
	Subsystem: 13d0:2103
	Flags: bus master, slow devsel, latency 64, IRQ 17
	Memory at fdbe0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at ef00 [size=32]
	Kernel driver in use: b2c2_flexcop_pci
	Kernel modules: b2c2-flexcop-pci

**dmesg | grep -i dvb **

[    7.990431] dvb_init() allocating 1 frontend
[    7.996208] DVB: registering new adapter (FlexCop Digital TV device)
[    8.629505] b2c2-flexcop: found 'ST STV0299 DVB-S' .
[    8.629511] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
[    8.629568] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.6' at the 'PCI' bus controlled by a 'FlexCopIIb' complete

and it's a small part of dmesg log in 9.04

13.112187] DVB: registering new adapter (FlexCop Digital TV device)
[   13.161251] dvb_init() allocating 1 frontend
[   13.180201] DVB: registering new adapter (saa7133[0])
[   13.180208] DVB: registering adapter 1 frontend 0 (Philips TDA10046H DVB-T)...
[   13.383589] b2c2-flexcop: found 'ST STV0299 DVB-S' .
[   13.383616] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...
[   13.383692] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S rev 2.6' at the 'PCI' bus controlled by a 'FlexCopIIb' complete
[   61.831409] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)
[   65.881254] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)
[   87.559812] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)
[   94.011522] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)
[   99.070896] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)
[  103.353274] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)
[  108.437371] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)
[  123.492862] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)
[  271.907101] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)
[ 5351.131735] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)

---

### Post by anthony2010 on 2009-11-30
Ringi!

The card is now seen ( Thanks!) however whenever I click a channel, Kaffeine gives an error message:

'Cannot find demultiplexer plugin for the given media data'

What does this mean? I need this in order to start viewing?

Cheers,

ant.

---

### Post by anthony2010 on 2009-11-30
Ringi

Ignore last post. Kaffeine doesnt work for tv but MeTv does. (rubbish picture though!) all lines on horizontal plane. Will see if there are twiddly things I can do to fix that.

For me it appears the situation is solved but I note another post on this thread.

Many, many thanks.

ant.

---

### Post by algiux1 on 2009-12-01
anyone any ideas?maybe some new firmware needs to be installed for this card?

---

### Post by anthony2010 on 2009-12-01
Hey,

If you look at an earlier post, I was instructed to type dmseg in the terminal. I did that and as you can see the terminal told me the driver it needed (firmware?) The only thing I can think is you do that, see if you get what driver is needed and see what you can google on that driver.

good luck.

ant

---

### Post by algiux1 on 2009-12-03
yesterday tried to install-reinstall v4l drivers as well as linux-firmware-nonfree with no results.there is some script to extract firmware from windows drivers.that's the only thing left to try.i noticed some diference in subsystem numbers of supported cards by this kernel.for example card=114 (kworld 210) has 17de:7250 and the one my card has got is 17de:7253.is it important?and Ringi in some post wrote he;s got the newest firmware of dvb-fe-tda10046 does it mean that new cards must use up to date firmware to work in karmic?

---

### Post by Cresho on 2009-12-03
```
sudo apt-get install libxine1-ffmpeg libavcodec-unstripped-52 xine-ui
```


then run kaffein, select region, scan, watch tv

---

### Post by Cresho on 2009-12-03
try again with me-tv.  install me-tv

then

```
sudo apt-get install dvb-apps
mkdir ~/.azap
scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB > ~/.azap/channels.conf
```

open up me-tv after all the scanning is done.  it will tell you in terminal

open up gedit text editor, go into your .azap directory and drag and drop that conf into the text editor, safe the file as same name but make sure you select
 utf-8 cuz me-tv hates western.
then tell me tv to use the channel.conf created by the utility and that file is in your home directory in .azap.  open up nautilus and view hidden folders, you will see it there.  tell me-tv to use that file to import channels.

---

### Post by amster on 2013-01-09
I'm new to this thread having just installed an Avermedia Hybrid pci card in my PC. PC dual boots with Ubuntu 12.04 and Windows 7, both 64 bit. Under Windows the card works perfectly with both picture and sound. Under Ubuntu using TVtime I have a good picture but no sound. Alsamixer recognises the card but no matter what inputs I un-mute I still cannot get any sound output. Sound works for all other devices & progs.

sudo lspci -vvnn gives:

04:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
    Subsystem: Avermedia Technologies Inc Hybrid+FM PCI (rev A16D) [1461:f936]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: saa7134
    Kernel modules: saa7134

Any suggestions please?

---


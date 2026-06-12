---
title: "Crappy Graffics in Ubuntu 10.10 how to upgrade"
date: 2011-07-21
forum: Multimedia Software
---

### Post by 4042966262 on 2011-07-21
heres the deal, useing Linux Slitaz I had pretty good Flash played smoothly and clear.
on Ubuntu however flash skips, and any content is slow.
i think my Driver Graphics are not sut up right,  

here are Computer Specifications [http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/12454-12454-3329737-89304-89304-5035288-5057709.html](http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/12454-12454-3329737-89304-89304-5035288-5057709.html)

it says I have a Intel Graphics Media Accelerator X4500 (up to 270 MB)
how can i fix this?

---

### Post by 4042966262 on 2011-07-21
```

```coffee@coffee-Cup:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Memory behind bridge: f7000000-f7ffffff
    Prefetchable memory behind bridge: fc000000-fdffffff
    Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: fe000000-fe2fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12) (prog-if 80 [Master])
    Subsystem: Compaq Computer Corporation Device 2411
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    Region 4: I/O ports at 2480 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12) (prog-if 00 [UHCI])
    Subsystem: Compaq Computer Corporation Device 2411
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 19
    Region 4: I/O ports at 2440 [size=32]
    Kernel driver in use: uhci_hcd

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12) (prog-if 00 [UHCI])
    Subsystem: Compaq Computer Corporation Device 2411
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 23
    Region 4: I/O ports at 2460 [size=32]
    Kernel driver in use: uhci_hcd

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
    Subsystem: Compaq Computer Corporation Device 008a
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 17
    Region 0: I/O ports at 2000 [size=256]
    Region 1: I/O ports at 2400 [size=64]
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15) (prog-if 00 [VGA controller])
    Subsystem: nVidia Corporation Device 0072
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (1250ns min, 250ns max)
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at fc000000 (32-bit, prefetchable) [size=32M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidia-current, nouveau, nvidiafb, rivafb

02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
    Subsystem: Compaq Computer Corporation EtherExpress PRO/100 VM
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 66 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at fe200000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at 1000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

02:09.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 04 [Hayes/16750])
    Subsystem: PCTel Inc Device 0001
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 1040 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: serial```

```

---

### Post by Toz on 2011-07-21
> **4042966262 said:**
> heres the deal, useing Linux Slitaz I had pretty good Flash played smoothly and clear.
on Ubuntu however flash skips, and any content is slow.
i think my Driver Graphics are not sut up right,  

here are Computer Specifications [http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/12454-12454-3329737-89304-89304-5035288-5057709.html](http://h10010.www1.hp.com/wwpc/in/en/ho/WF06b/12454-12454-3329737-89304-89304-5035288-5057709.html)

it says I have a Intel Graphics Media Accelerator X4500 (up to 270 MB)
how can i fix this?

According to your second post, it contains an nvidia card. 
> 01:00.0 VGA compatible controller: [COLOR="Red"]nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)[/COLOR] (prog-if 00 [VGA controller])
Subsystem: nVidia Corporation Device 0072
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
Latency: 64 (1250ns min, 250ns max)
Interrupt: pin A routed to IRQ 18
Region 0: Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
Region 1: Memory at fc000000 (32-bit, prefetchable) [size=32M]
Expansion ROM at <unassigned> [disabled]
Capabilities: <access denied>
Kernel driver in use: [COLOR="red"]nouveau[/COLOR]
Kernel modules: nvidia-current, nouveau, nvidiafb, rivafb

It also states that you are using the open source nouveau driver. Do you have the proprietary driver available in the Additional Drivers program? [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by 4042966262 on 2011-07-22
''Nouveau, an open source driver, is installed by default.''
Since this is a new install I'm pretty sure its installed. what do you recommend I do?
[IMG]http://i55.tinypic.com/2lnak8w.jpg[/IMG]

[http://tinypic.com/r/2lnak8w/7](http://tinypic.com/r/2lnak8w/7)

---

### Post by Toz on 2011-07-22
Try removing the nouveau driver. 
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```
Reference Link: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by 4042966262 on 2011-07-22
coffee@coffee-Cup:~$ sudo apt-get --purge remove xserver-xorg-video-nouveau
[sudo] password for coffee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xserver-xorg-video-all* xserver-xorg-video-nouveau*
0 upgraded, 0 newly installed, 2 to remove and 351 not upgraded.
After this operation, 315kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 124572 files and directories currently installed.)
Removing xserver-xorg-video-all ...
Removing xserver-xorg-video-nouveau ...
Processing triggers for man-db ...
coffee@coffee-Cup:~$ 

Now what?

---

### Post by Toz on 2011-07-22
Try rebooting and post back **lspci -vnn** and the contents of **/var/log/Xorg.0.log** again.

---

### Post by 4042966262 on 2011-07-24
```

```coffee@coffee-Cup:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: f7000000-f7ffffff
	Prefetchable memory behind bridge: fc000000-fdffffff
	Kernel modules: shpchp

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 12) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: fe000000-fe2fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 12)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 12) (prog-if 80 [Master])
	Subsystem: Compaq Computer Corporation Device [0e11:2411]
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at 2480 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 12) (prog-if 00 [UHCI])
	Subsystem: Compaq Computer Corporation Device [0e11:2411]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 2440 [size=32]
	Kernel driver in use: uhci_hcd

00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 12) (prog-if 00 [UHCI])
	Subsystem: Compaq Computer Corporation Device [0e11:2411]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 2460 [size=32]
	Kernel driver in use: uhci_hcd

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 12)
	Subsystem: Compaq Computer Corporation Device [0e11:008a]
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 2000 [size=256]
	I/O ports at 2400 [size=64]
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV6 [Vanta/Vanta LT] [10de:002c] (rev 15) (prog-if 00 [VGA controller])
	Subsystem: nVidia Corporation Device [10de:0072]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
	Memory at fc000000 (32-bit, prefetchable) [size=32M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel modules: nvidia-current, nouveau, nvidiafb, rivafb

02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
	Subsystem: Compaq Computer Corporation EtherExpress PRO/100 VM [0e11:0012]
	Flags: bus master, medium devsel, latency 66, IRQ 20
	Memory at fe200000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

02:09.0 Modem [0703]: PCTel Inc HSP MicroModem 56 [134d:7897] (rev 02) (prog-if 04 [Hayes/16750])
	Subsystem: PCTel Inc Device [134d:0001]
	Flags: medium devsel, IRQ 18
	I/O ports at 1040 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: serial


bash: /var/log/Xorg.0.log: Permission denied
coffee@coffee-Cup:~$```

```

---

### Post by Toz on 2011-07-24
/var/log/Xorg.0.log is a file. You can open it with an editor like gedit, or display the contents like:
```
cat /var/log/Xorg.0.log
```Please post back the contents inside code tags (see: [http://ubuntuforums.org/misc.php?do=bbcode]("http://ubuntuforums.org/misc.php?do=bbcode")).

Are the graphics working better?

---

### Post by 4042966262 on 2011-07-25
wow feel dumb...

```
[CODE][    36.780] (II) NV(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
[    36.780] (**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[    36.780] (II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    36.780] (**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[    36.780] (II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[    36.780] (**) NV(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
[    36.780] (II) NV(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
[    36.780] (**) NV(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
[    36.780] (II) NV(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
[    36.781] (**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[    36.781] (II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[    36.781] (**) NV(0): Display dimensions: (340, 270) mm
[    36.781] (**) NV(0): DPI set to (95, 96)
[    36.781] (II) Loading sub module "fb"
[    36.781] (II) LoadModule: "fb"
[    36.782] (II) Loading /usr/lib/xorg/modules/libfb.so
[    36.782] (II) Module fb: vendor="X.Org Foundation"
[    36.782] 	compiled for 1.9.0, module version = 1.0.0
[    36.782] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    36.783] (II) Loading sub module "xaa"
[    36.783] (II) LoadModule: "xaa"
[    36.783] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    36.788] (II) Module xaa: vendor="X.Org Foundation"
[    36.788] 	compiled for 1.9.0, module version = 1.2.1
[    36.788] 	ABI class: X.Org Video Driver, version 8.0
[    36.788] (II) Loading sub module "ramdac"
[    36.788] (II) LoadModule: "ramdac"
[    36.788] (II) Module "ramdac" already built-in
[    36.789] (II) UnloadModule: "vesa"
[    36.789] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    36.789] (II) UnloadModule: "fbdev"
[    36.789] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    36.789] (II) UnloadModule: "fbdevhw"
[    36.789] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    36.789] (--) Depth 24 pixmap format is 32 bpp
[    37.120] (II) NV(0): Using XFree86 Acceleration Architecture (XAA)
[    37.266] 	Screen to screen bit blits
[    37.266] 	Solid filled rectangles
[    37.266] 	8x8 mono pattern filled rectangles
[    37.266] 	Indirect CPU to Screen color expansion
[    37.266] 	Solid Lines
[    37.266] 	Scanline Image Writes
[    37.267] 	Setting up tile and stipple cache:
[    37.267] 		32 128x128 slots
[    37.267] 		14 256x256 slots
[    37.267] 		5 512x512 slots
[    37.267] (==) NV(0): Backing store disabled
[    37.267] (==) NV(0): Silken mouse enabled
[    37.269] (==) NV(0): DPMS enabled
[    37.269] (==) RandR enabled
[    37.269] (II) Initializing built-in extension Generic Event Extension
[    37.269] (II) Initializing built-in extension SHAPE
[    37.269] (II) Initializing built-in extension MIT-SHM
[    37.269] (II) Initializing built-in extension XInputExtension
[    37.269] (II) Initializing built-in extension XTEST
[    37.269] (II) Initializing built-in extension BIG-REQUESTS
[    37.269] (II) Initializing built-in extension SYNC
[    37.269] (II) Initializing built-in extension XKEYBOARD
[    37.269] (II) Initializing built-in extension XC-MISC
[    37.269] (II) Initializing built-in extension SECURITY
[    37.269] (II) Initializing built-in extension XINERAMA
[    37.269] (II) Initializing built-in extension XFIXES
[    37.269] (II) Initializing built-in extension RENDER
[    37.269] (II) Initializing built-in extension RANDR
[    37.269] (II) Initializing built-in extension COMPOSITE
[    37.269] (II) Initializing built-in extension DAMAGE
[    37.269] (II) Initializing built-in extension GESTURE
[    37.279] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    37.357] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.379] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    37.379] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.379] (II) LoadModule: "evdev"
[    37.380] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.381] (II) Module evdev: vendor="X.Org Foundation"
[    37.381] 	compiled for 1.9.0, module version = 2.3.2
[    37.381] 	Module class: X.Org XInput Driver
[    37.381] 	ABI class: X.Org XInput driver, version 11.0
[    37.381] (**) Power Button: always reports core events
[    37.381] (**) Power Button: Device: "/dev/input/event1"
[    37.382] (II) Power Button: Found keys
[    37.382] (II) Power Button: Configuring as keyboard
[    37.382] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    37.382] (**) Option "xkb_rules" "evdev"
[    37.382] (**) Option "xkb_model" "pc105"
[    37.382] (**) Option "xkb_layout" "us"
[    37.385] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    37.386] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.386] (**) Power Button: always reports core events
[    37.386] (**) Power Button: Device: "/dev/input/event0"
[    37.386] (II) Power Button: Found keys
[    37.386] (II) Power Button: Configuring as keyboard
[    37.386] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    37.386] (**) Option "xkb_rules" "evdev"
[    37.386] (**) Option "xkb_model" "pc105"
[    37.386] (**) Option "xkb_layout" "us"
[    37.395] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[    37.395] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[    37.395] (**) Logitech Trackball: always reports core events
[    37.395] (**) Logitech Trackball: Device: "/dev/input/event2"
[    37.396] (II) Logitech Trackball: Found 3 mouse buttons
[    37.396] (II) Logitech Trackball: Found scroll wheel(s)
[    37.396] (II) Logitech Trackball: Found relative axes
[    37.396] (II) Logitech Trackball: Found x and y relative axes
[    37.396] (II) Logitech Trackball: Configuring as mouse
[    37.396] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[    37.396] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.396] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[    37.396] (II) Logitech Trackball: initialized for relative axes.
[    37.397] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[    37.398] (II) No input driver/identifier specified (ignoring)
[    37.400] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event3)
[    37.400] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[    37.400] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[    37.400] (**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event3"
[    37.400] (II) Logitech Logitech BT Mini-Receiver: Found keys
[    37.400] (II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[    37.400] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
[    37.400] (**) Option "xkb_rules" "evdev"
[    37.400] (**) Option "xkb_model" "pc105"
[    37.400] (**) Option "xkb_layout" "us"
[    37.405] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/event4)
[    37.405] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev pointer catchall"
[    37.405] (**) Logitech Logitech BT Mini-Receiver: Applying InputClass "evdev keyboard catchall"
[    37.405] (**) Logitech Logitech BT Mini-Receiver: always reports core events
[    37.405] (**) Logitech Logitech BT Mini-Receiver: Device: "/dev/input/event4"
[    37.406] (II) Logitech Logitech BT Mini-Receiver: Found 16 mouse buttons
[    37.406] (II) Logitech Logitech BT Mini-Receiver: Found scroll wheel(s)
[    37.406] (II) Logitech Logitech BT Mini-Receiver: Found relative axes
[    37.406] (II) Logitech Logitech BT Mini-Receiver: Found x and y relative axes
[    37.406] (II) Logitech Logitech BT Mini-Receiver: Found absolute axes
[    37.407] (II) evdev-grail: failed to open grail, no gesture support
[    37.407] (II) Logitech Logitech BT Mini-Receiver: Found keys
[    37.407] (II) Logitech Logitech BT Mini-Receiver: Configuring as mouse
[    37.407] (II) Logitech Logitech BT Mini-Receiver: Configuring as keyboard
[    37.407] (**) Logitech Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
[    37.407] (**) Logitech Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.407] (II) XINPUT: Adding extended input device "Logitech Logitech BT Mini-Receiver" (type: KEYBOARD)
[    37.407] (**) Option "xkb_rules" "evdev"
[    37.407] (**) Option "xkb_model" "pc105"
[    37.407] (**) Option "xkb_layout" "us"
[    37.408] (II) Logitech Logitech BT Mini-Receiver: initialized for relative axes.
[    37.408] (WW) Logitech Logitech BT Mini-Receiver: ignoring absolute axes.
[    37.411] (II) config/udev: Adding input device Logitech Logitech BT Mini-Receiver (/dev/input/mouse1)
[    37.411] (II) No input driver/identifier specified (ignoring)
[    41.902] (II) config/udev: removing device Logitech Trackball
[    41.903] (II) Logitech Trackball: Close
[    41.903] (II) UnloadModule: "evdev"
[    84.700] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[    84.700] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[    84.700] (**) Logitech Trackball: always reports core events
[    84.700] (**) Logitech Trackball: Device: "/dev/input/event2"
[    84.700] (II) Logitech Trackball: Found 3 mouse buttons
[    84.700] (II) Logitech Trackball: Found scroll wheel(s)
[    84.700] (II) Logitech Trackball: Found relative axes
[    84.700] (II) Logitech Trackball: Found x and y relative axes
[    84.701] (II) Logitech Trackball: Configuring as mouse
[    84.701] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[    84.701] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    84.701] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[    84.701] (II) Logitech Trackball: initialized for relative axes.
[    84.711] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[    84.711] (II) No input driver/identifier specified (ignoring)
[    86.467] (II) config/udev: removing device Logitech Trackball
[    86.467] (II) Logitech Trackball: Close
[    86.467] (II) UnloadModule: "evdev"
[    86.936] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[    86.936] (II) No input driver/identifier specified (ignoring)
[    86.943] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[    86.943] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[    86.944] (**) Logitech Trackball: always reports core events
[    86.944] (**) Logitech Trackball: Device: "/dev/input/event2"
[    86.944] (II) Logitech Trackball: Found 3 mouse buttons
[    86.944] (II) Logitech Trackball: Found scroll wheel(s)
[    86.944] (II) Logitech Trackball: Found relative axes
[    86.944] (II) Logitech Trackball: Found x and y relative axes
[    86.944] (II) Logitech Trackball: Configuring as mouse
[    86.944] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[    86.944] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    86.944] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[    86.944] (II) Logitech Trackball: initialized for relative axes.
[    87.218] (II) config/udev: removing device Logitech Trackball
[    87.219] (II) Logitech Trackball: Close
[    87.219] (II) UnloadModule: "evdev"
[    87.873] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[    87.873] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[    87.873] (**) Logitech Trackball: always reports core events
[    87.873] (**) Logitech Trackball: Device: "/dev/input/event2"
[    87.873] (II) Logitech Trackball: Found 3 mouse buttons
[    87.873] (II) Logitech Trackball: Found scroll wheel(s)
[    87.873] (II) Logitech Trackball: Found relative axes
[    87.873] (II) Logitech Trackball: Found x and y relative axes
[    87.873] (II) Logitech Trackball: Configuring as mouse
[    87.873] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[    87.873] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    87.874] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[    87.874] (II) Logitech Trackball: initialized for relative axes.
[    87.884] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[    87.884] (II) No input driver/identifier specified (ignoring)
[   139.654] (II) config/udev: removing device Logitech Trackball
[   139.655] (II) Logitech Trackball: Close
[   139.655] (II) UnloadModule: "evdev"
[   143.554] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   143.554] (II) No input driver/identifier specified (ignoring)
[   143.561] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   143.561] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   143.561] (**) Logitech Trackball: always reports core events
[   143.561] (**) Logitech Trackball: Device: "/dev/input/event2"
[   143.561] (II) Logitech Trackball: Found 3 mouse buttons
[   143.561] (II) Logitech Trackball: Found scroll wheel(s)
[   143.561] (II) Logitech Trackball: Found relative axes
[   143.561] (II) Logitech Trackball: Found x and y relative axes
[   143.561] (II) Logitech Trackball: Configuring as mouse
[   143.562] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   143.562] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   143.562] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   143.562] (II) Logitech Trackball: initialized for relative axes.
[   143.762] (II) config/udev: removing device Logitech Trackball
[   143.762] (II) Logitech Trackball: Close
[   143.762] (II) UnloadModule: "evdev"
[   144.640] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   144.641] (II) No input driver/identifier specified (ignoring)
[   144.648] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   144.648] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   144.648] (**) Logitech Trackball: always reports core events
[   144.648] (**) Logitech Trackball: Device: "/dev/input/event2"
[   144.648] (II) Logitech Trackball: Found 3 mouse buttons
[   144.648] (II) Logitech Trackball: Found scroll wheel(s)
[   144.648] (II) Logitech Trackball: Found relative axes
[   144.648] (II) Logitech Trackball: Found x and y relative axes
[   144.649] (II) Logitech Trackball: Configuring as mouse
[   144.649] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   144.649] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   144.649] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   144.649] (II) Logitech Trackball: initialized for relative axes.
[   145.002] (II) config/udev: removing device Logitech Trackball
[   145.002] (II) Logitech Trackball: Close
[   145.002] (II) UnloadModule: "evdev"
[   146.349] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   146.349] (II) No input driver/identifier specified (ignoring)
[   146.356] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   146.356] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   146.356] (**) Logitech Trackball: always reports core events
[   146.356] (**) Logitech Trackball: Device: "/dev/input/event2"
[   146.356] (II) Logitech Trackball: Found 3 mouse buttons
[   146.356] (II) Logitech Trackball: Found scroll wheel(s)
[   146.356] (II) Logitech Trackball: Found relative axes
[   146.357] (II) Logitech Trackball: Found x and y relative axes
[   146.357] (II) Logitech Trackball: Configuring as mouse
[   146.357] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   146.357] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   146.357] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   146.357] (II) Logitech Trackball: initialized for relative axes.
[   157.393] (II) config/udev: removing device Logitech Trackball
[   157.393] (II) Logitech Trackball: Close
[   157.394] (II) UnloadModule: "evdev"
[   157.876] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   157.877] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   157.877] (**) Logitech Trackball: always reports core events
[   157.877] (**) Logitech Trackball: Device: "/dev/input/event2"
[   157.877] (II) Logitech Trackball: Found 3 mouse buttons
[   157.877] (II) Logitech Trackball: Found scroll wheel(s)
[   157.877] (II) Logitech Trackball: Found relative axes
[   157.877] (II) Logitech Trackball: Found x and y relative axes
[   157.877] (II) Logitech Trackball: Configuring as mouse
[   157.877] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   157.877] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   157.877] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   157.877] (II) Logitech Trackball: initialized for relative axes.
[   157.889] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   157.889] (II) No input driver/identifier specified (ignoring)
[   210.482] (II) config/udev: removing device Logitech Trackball
[   210.483] (II) Logitech Trackball: Close
[   210.483] (II) UnloadModule: "evdev"
[   212.411] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   212.411] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   212.411] (**) Logitech Trackball: always reports core events
[   212.411] (**) Logitech Trackball: Device: "/dev/input/event2"
[   212.411] (II) Logitech Trackball: Found 3 mouse buttons
[   212.411] (II) Logitech Trackball: Found scroll wheel(s)
[   212.411] (II) Logitech Trackball: Found relative axes
[   212.411] (II) Logitech Trackball: Found x and y relative axes
[   212.411] (II) Logitech Trackball: Configuring as mouse
[   212.411] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   212.414] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   212.414] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   212.414] (II) Logitech Trackball: initialized for relative axes.
[   212.433] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   212.433] (II) No input driver/identifier specified (ignoring)
[   248.658] (II) config/udev: removing device Logitech Trackball
[   248.659] (II) Logitech Trackball: Close
[   248.659] (II) UnloadModule: "evdev"
[   251.558] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   251.558] (II) No input driver/identifier specified (ignoring)
[   251.566] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   251.566] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   251.566] (**) Logitech Trackball: always reports core events
[   251.566] (**) Logitech Trackball: Device: "/dev/input/event2"
[   251.567] (II) Logitech Trackball: Found 3 mouse buttons
[   251.567] (II) Logitech Trackball: Found scroll wheel(s)
[   251.567] (II) Logitech Trackball: Found relative axes
[   251.567] (II) Logitech Trackball: Found x and y relative axes
[   251.567] (II) Logitech Trackball: Configuring as mouse
[   251.567] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   251.567] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   251.567] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   251.567] (II) Logitech Trackball: initialized for relative axes.
[   254.115] (II) config/udev: removing device Logitech Trackball
[   254.116] (II) Logitech Trackball: Close
[   254.116] (II) UnloadModule: "evdev"
[   263.552] (II) config/udev: Adding input device (unnamed) (/dev/input/mouse0)
[   263.552] (II) No input driver/identifier specified (ignoring)
[   263.564] (II) config/udev: Adding input device (unnamed) (/dev/input/event2)
[   263.564] (**) (unnamed): Applying InputClass "evdev pointer catchall"
[   263.564] (**) (unnamed): always reports core events
[   263.564] (**) (unnamed): Device: "/dev/input/event2"
[   263.564] (EE) Unable to open evdev device "/dev/input/event2".
[   263.564] (II) UnloadModule: "evdev"
[   263.564] (EE) PreInit returned NULL for "(unnamed)"
[   264.077] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   264.077] (II) No input driver/identifier specified (ignoring)
[   264.084] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   264.085] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   264.085] (**) Logitech Trackball: always reports core events
[   264.085] (**) Logitech Trackball: Device: "/dev/input/event2"
[   264.085] (II) Logitech Trackball: Found 3 mouse buttons
[   264.085] (II) Logitech Trackball: Found scroll wheel(s)
[   264.085] (II) Logitech Trackball: Found relative axes
[   264.085] (II) Logitech Trackball: Found x and y relative axes
[   264.085] (II) Logitech Trackball: Configuring as mouse
[   264.085] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   264.085] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   264.085] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   264.085] (II) Logitech Trackball: initialized for relative axes.
[   266.522] (II) config/udev: removing device Logitech Trackball
[   266.523] (II) Logitech Trackball: Close
[   266.523] (II) UnloadModule: "evdev"
[   300.720] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   300.720] (II) No input driver/identifier specified (ignoring)
[   300.728] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   300.728] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   300.728] (**) Logitech Trackball: always reports core events
[   300.728] (**) Logitech Trackball: Device: "/dev/input/event2"
[   300.729] (II) Logitech Trackball: Found 3 mouse buttons
[   300.729] (II) Logitech Trackball: Found scroll wheel(s)
[   300.729] (II) Logitech Trackball: Found relative axes
[   300.729] (II) Logitech Trackball: Found x and y relative axes
[   300.729] (II) Logitech Trackball: Configuring as mouse
[   300.729] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   300.729] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   300.729] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   300.729] (II) Logitech Trackball: initialized for relative axes.
[   302.739] (II) config/udev: removing device Logitech Trackball
[   302.740] (II) Logitech Trackball: Close
[   302.740] (II) UnloadModule: "evdev"
[   304.206] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   304.206] (II) No input driver/identifier specified (ignoring)
[   304.214] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   304.214] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   304.214] (**) Logitech Trackball: always reports core events
[   304.214] (**) Logitech Trackball: Device: "/dev/input/event2"
[   304.215] (II) Logitech Trackball: Found 3 mouse buttons
[   304.215] (II) Logitech Trackball: Found scroll wheel(s)
[   304.215] (II) Logitech Trackball: Found relative axes
[   304.215] (II) Logitech Trackball: Found x and y relative axes
[   304.215] (II) Logitech Trackball: Configuring as mouse
[   304.215] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   304.215] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   304.215] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   304.215] (II) Logitech Trackball: initialized for relative axes.
[   306.963] (II) config/udev: removing device Logitech Trackball
[   306.964] (II) Logitech Trackball: Close
[   306.964] (II) UnloadModule: "evdev"
[   307.461] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   307.461] (II) No input driver/identifier specified (ignoring)
[   307.469] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   307.469] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   307.469] (**) Logitech Trackball: always reports core events
[   307.469] (**) Logitech Trackball: Device: "/dev/input/event2"
[   307.469] (II) Logitech Trackball: Found 3 mouse buttons
[   307.469] (II) Logitech Trackball: Found scroll wheel(s)
[   307.469] (II) Logitech Trackball: Found relative axes
[   307.469] (II) Logitech Trackball: Found x and y relative axes
[   307.469] (II) Logitech Trackball: Configuring as mouse
[   307.469] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   307.470] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   307.470] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   307.470] (II) Logitech Trackball: initialized for relative axes.
[   308.451] (II) config/udev: removing device Logitech Trackball
[   308.452] (II) Logitech Trackball: Close
[   308.452] (II) UnloadModule: "evdev"
[   310.164] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[   310.164] (II) No input driver/identifier specified (ignoring)
[   310.171] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event2)
[   310.172] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[   310.172] (**) Logitech Trackball: always reports core events
[   310.172] (**) Logitech Trackball: Device: "/dev/input/event2"
[   310.172] (II) Logitech Trackball: Found 3 mouse buttons
[   310.172] (II) Logitech Trackball: Found scroll wheel(s)
[   310.172] (II) Logitech Trackball: Found relative axes
[   310.172] (II) Logitech Trackball: Found x and y relative axes
[   310.172] (II) Logitech Trackball: Configuring as mouse
[   310.172] (**) Logitech Trackball: YAxisMapping: buttons 4 and 5
[   310.172] (**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   310.172] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
[   310.172] (II) Logitech Trackball: initialized for relative axes.
coffee@coffee-Cup:~$ 

```[/CODE]

---

### Post by Toz on 2011-07-25
Somethings not right. Go back to Additional Drivers and remove the nvidia driver. Reboot. Then go back again to Additional Drivers and re-enable it. Reboot once more. Paste back /var/log/Xorg.0.log. The last paste was not the complete contents of the file. Open it like this:
```
gedit /var/log/Xorg.0.log
```
copy everything and paste again in only one set of CODE blocks.

---


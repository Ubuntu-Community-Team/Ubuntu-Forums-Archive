---
title: "Configuring X + Xinerama"
date: 2006-03-19
forum: Multimedia &amp; Video
---

### Post by dcroxton on 2006-03-19
I have an ASRock P4i45GV motherboard, which has onboard video + an open slop, for what is supposedly "easy dual monitor."  I didn't really believe that :), but I do hope I can make it work eventually.

I plugged in a new video card (actually kind of an old one, AGP-v7100) and right away the display worked, although booting kept hanging at "starting hotplug system" until I changed the default display back to the onboard video.  Then I tried following the instructions at [www.tldp.org/HOWTO/Xinerama-HOWTO](www.tldp.org/HOWTO/Xinerama-HOWTO).  First problem, I couldn't find the config file /etc/X11/XF86Config that he referred to, so I backed up the whole /etc/X11 directory.  Then I stopped gdm and tried running "X -configure."  Second problem, this failed with the following message toward the end:

[INDENT](II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corp. 82845G/GL [Brookdale-G] Chipset Integrated Graphics Device rev 3, Mem @ 0xd0000000/27, 0xdff80000/19
(--) PCI: (3:0:0) nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] rev 178, Mem @ 0xde000000/24, 0xc0000000/27, BIOS @ 0xdfdf0000/16
(--) PCI: (3:4:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @
0xc8000000/26
Missing output drivers.  Configuration failed.
[/INDENT]

I'm pretty clueless about how to proceed, so any advice will be appreciated.

Sincerely,
Derek

---

### Post by fimbulvetr on 2006-03-19
First, get rid of the XF86config. (mv XF86Config XF86Config.old) You must have found an older howto. They don't use XF86Config anymore, they use xorg.conf.

Then, copy your xorg.conf to xorg.conf.working (just in case you mess it up, you now have a backup).

There are three additions and one modification you need in an xorg.conf to have a working Xinerama.

The first is a device section for your new card. Since your new card is a geforce mx400, you should make it something like this: (Keep it simple at first, enough to get it working):

```

Section "Device"
    Identifier     "AGP7100"
    Driver         "nv"
EndSection

```

Now, you need a screen section. I can't give you much guidance on this, but if it's the exact same monitor as your other one, just copy the "Section "Screen"...EndSection" stuff and change your Identifier line from "default screen" to "default screen 2".

Also, in the new Screen section make sure you have a line like this:
```

Device      "AGP7100"

```

(Which tells the screen you just made to use that Device (video card) you just made.)
Now, it doesn't matter where, add this to your file:

```

Section "ServerFlags"
  Option "Xinerama" "true"
EndSection

```

The 4th change is pretty simple.

Find the section like this:

```

Section "ServerLayout"
        Identifier "Single"
        Screen "Default Screen"
        InputDevice "Mouse1" "CorePointer"
        InputDevice "Keyboard1" "CoreKeyboard"
EndSection

```

and make it look something like this:

```

Section "ServerLayout"
        Identifier "Dual"
        Screen "Default Screen"
        Screen "Default Screen 2" LeftOf "Default Screen"
        InputDevice "Mouse1" "CorePointer"
        InputDevice "Keyboard1" "CoreKeyboard"
EndSection

```

Restart X/Your computer.

Easy and sleezy!

---

### Post by dcroxton on 2006-03-19
Thanks for your quick response!  The first time, it complained about an un-referenced monitor, so I added a "monitor" section.  Then it booted & started X fine, but I have no indication that the second screen is doing anything.  Two notes:

(a) I copied the "monitor" and "screen" section from a Xandros 2.0 computer that was configured for the second monitor originally (now it's just a server with no monitor).  I figure that's probably pretty accurate, although it still uses an XF86Conf-4 config file, so maybe some things are out of date.

(b) Here's a big chunk of the X log, if that might help; or let me know if you need all of it:

[INDENT](II) I810(0): XF-9bi: Using default hsync range of 30.00-86.00 kHz
(II) I810(0): XF-9bi: Using default vrefresh range of 50.00-160.00 Hz
(II) I810(0): Not using mode "720x400" (no mode of this name)
(720x400,XF-9bi) mode clock 100000MHz exceeds DDC maximum 150MHz
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(--) I810(0): Virtual size is 1280x1024 (pitch 2048)
(**) I810(0): *Built-in mode "1280x1024"
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(II) I810(0): Attempting to use 75.02Hz refresh for mode "1280x1024" (858)
(II) I810(0): Attempting to use 85.00Hz refresh for mode "1024x768" (854)
(II) I810(0): Attempting to use 85.14Hz refresh for mode "800x600" (852)
(II) I810(0): Attempting to use 85.01Hz refresh for mode "640x480" (850)
(--) I810(0): Display dimensions: (370, 270) mm
(--) I810(0): DPI set to (87, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/X11R6/lib/modules/libshadow.a
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) UnloadModule: "nv"
(II) Unloading /usr/X11R6/lib/modules/drivers/nv_drv.o
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdff80000 - 0xdfffffff (0x80000) MS[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MS[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x2f7fffff (0x2f700000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdfdeff00 - 0xdfdeffff (0x100) MX[B]
	[8] -1	0	0xdff7b900 - 0xdff7b9ff (0x100) MX[B]
	[9] -1	0	0xdff7ba00 - 0xdff7bbff (0x200) MX[B]
	[10] -1	0	0x2f800000 - 0x2f8003ff (0x400) MX[B]
	[11] -1	0	0xdff7bc00 - 0xdff7bfff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xc8000000 - 0xcbffffff (0x4000000) MX[B](B)
	[14] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[18] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc3f (0x40) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)845G/845GL/845GE/845GV Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Before: SWF1 is 0x00000000
(II) I810(0): After: SWF1 is 0x00000008
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 256 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 10240 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0x7fff000
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0x7ffb000
(II) I810(0): Allocated 4 kB for Overlay registers at 0x7ffa000 (0x25bac000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0x7fea000
(II) I810(0): Updated framebuffer allocation size from 10240 to 16384 kByte
(II) I810(0): Updated pixmap cache from 256 scanlines to 1024 scanlines
(II) I810(0): 0x83f37bc: Memory at offset 0x00020000, size 16384 kBytes
(II) I810(0): 0x83ad9a0: Memory at offset 0x07fff000, size 4 kBytes
(II) I810(0): 0x83ad9c8: Memory at offset 0x07ffb000, size 16 kBytes
(II) I810(0): 0x83a221c: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x83f37fc: Memory at offset 0x07fea000, size 64 kBytes
(II) I810(0): 0x83b0080: Memory at offset 0x07ffa000, size 4 kBytes
(==) I810(0): Write-combining range (0xd0000000,0x8000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x007df000 (pgoffset 2015)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x07fff000 (pgoffset 32767)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x07ffb000 (pgoffset 32763)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x07fea000 (pgoffset 32746)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x07ffa000 (pgoffset 32762)
(WW) I810(0): PGTBL_ER is 0x00000049
(II) I810(0): Before: SWF1 is 0x00001008
(II) I810(0): After: SWF1 is 0x00001008
(II) I810(0): Setting refresh with VBE 3 method.
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Enabling plane A.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): PIPEACONF is 0x80000000
(WW) I810(0): Correcting plane A stride (1280 -> 2048)
(II) I810(0): Mode bandwidth is 78 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 420 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		16 256x256 slots
		5 512x512 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): direct rendering: Failed
(==) RandR enabled
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
[/INDENT]

Sincerely,
Derek

---

### Post by dcroxton on 2006-03-21
For anyone else browsing this threat, I figured out how to get this working.  In addition to the excellent instructions from this thread, and adding the "monitor" section to xorg.conf, I also needed to add the BusID for the second video card.  I found this by using the "lspci" command and guessing which numbers were the right ones for the card. :)  (Actually, it was pretty obvious, but I would not have had a clue without the other BusID values to base it on.)

---


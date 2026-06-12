---
title: "Getting Beryl to work in i855"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by amb.physis on 2007-07-27
Hello people,

I am new to Ubuntu and new to Linux overall. I am trying to configure my 

```

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

```

card for the Beryl windows manager.

This is my xorg.conf (the part I think is relevant)

```

Section "Device"
        Identifier      "Tarjeta de vídeo genérica"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Monitor genérico"
        Option          "DPMS"
        HorizSync       28-96
        VertRefresh     43-60
EndSection

```

I am having problems with the GL stuff. This is the output of glxinfo

```

alex@laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

so this is as far as I can get.

also, the lshw gives

```

        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             size: 128MB
             width: 32 bits

```

I've been doing some research with no luck. By running the pdkg -reconfigure I've screwed my X a couple of times and already had to go back to the backup...

Does anybody have an idea?

Thanks in advance

---

### Post by amb.physis on 2007-07-27
Well, It seems I have isolated the problem. I cannot load dri neither glx modules. The Xorg.0.log file reads

```

(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 32576 kB
(II) intel(0): VESA VBE OEM: Intel(r)852GM/852GME/855GM/855GME Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)852GM/852GME/855GM/855GME Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(EE) intel(0): detecting sil164
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.

```

later on goes like

```

(II) intel(0): Kernel reported 104448 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 417788 kB available
(==) intel(0): VideoRam: 131072 KB
(EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 5472 scanlines for pixmap cache
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00027fff: logical 3D context (32 kB)
(II) intel(0): 0x00028000-0x00037fff: xaa scratch (64 kB)
(II) intel(0): 0x01fdf000:            end of stolen memory
(II) intel(0): 0x01fdf000-0x01fdffff: Core cursor (4 kB, 0x13b7f000 physical)
(II) intel(0): 0x01fe0000-0x01fe3fff: ARGB cursor (16 kB, 0x13bb8000 physical)
(II) intel(0): 0x01fe4000-0x01fe4fff: Core cursor (4 kB, 0x13b85000 physical)
(II) intel(0): 0x01fe5000-0x01fe8fff: ARGB cursor (16 kB, 0x13bbc000 physical)
(II) intel(0): 0x01ff0000-0x040e7fff: front buffer (33760 kB)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): front buffer is not tiled
(WW) intel(0): Disabling Xv because the overlay register buffer allocation failed.
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xe8000000,0x8000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01fdf000 (pgoffset 8159)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01fe0000 (pgoffset 8160)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01fe4000 (pgoffset 8164)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01fe5000 (pgoffset 8165)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x01ff0000 (pgoffset 8176)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TMDS is connected to pipe none
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): direct rendering: Disabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

I am using the xserver-xorg-video-intel driver and my xog.conf file is

```


Section "Device"
	Identifier	"Intel i855 Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i855 Integrated Graphics Device"
	Monitor		"Monitor genérico"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

while in the /usr/share/man/man4 has
```

root@laptop:/etc/X11# ls /usr/share/man/man4/
apm.4.gz            fd.4.gz      keyboard.4.gz   ptmx.4.gz           sisusb.4.gz     vcsa.4.gz
ati.4.gz            fifo.4.gz    kmem.4.gz       pts.4.gz            sk98lin.4.gz    vesa.4.gz
chips.4.gz          full.4.gz    lp.4.gz         r128.4.gz           st.4.gz         vga.4.gz
cirrus.4.gz         futex.4.gz   mem.4.gz        radeon.4.gz         tdfx.4.gz       via.4.gz
console.4.gz        glint.4.gz   mga.4.gz        ram.4.gz            trident.4.gz    vmware.4.gz
console_codes.4.gz  hd.4.gz      mouse.4.gz      random.4.gz         tseng.4.gz      voodoo.4.gz
console_ioctl.4.gz  i128.4.gz    mousedrv.4x.gz  rendition.4.gz      tty.4.gz        wacom.4x.gz
cyrix.4.gz          i740.4.gz    neomagic.4.gz   rtc.4.gz            tty_ioctl.4.gz  wavelan.4.gz
dsp56k.4.gz         imstt.4.gz   newport.4.gz    s3virge.4.gz        ttys.4.gz       zero.4.gz
elographics.4.gz    initrd.4.gz  nsc.4.gz        savage.4.gz         ttyS.4.gz
epoll.4.gz          **[COLOR="Red"]intel.4.gz[/COLOR]**   null.4.gz       sd.4.gz             urandom.4.gz
evdev.4.gz          intro.4.gz   nv.4.gz         siliconmotion.4.gz  v4l.4.gz
fbdev.4.gz          kbd.4.gz     port.4.gz       sis.4.gz            vcs.4.gz

```

although I only have the intel.4.gz file, apparently I am running on an i810 driver, according to xorg.conf.

Is this normal? Anyway, how can I get to load dri and glx modules??

Plesae Help!!

Thanx

---


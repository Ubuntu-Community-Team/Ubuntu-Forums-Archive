---
title: "fglrx = black screen, blinking Caps Lock"
date: 2009-11-03
forum: Multimedia Software
---

### Post by Lendro_Furioso on 2009-11-03
Ok, I'm trying this once again after posting a couple of times on other boards... So far I have to say I haven't gotten a whole lot of love from these boards regarding this problem, with yet a single reply, both from an older post when I ran Jaunty and a more recent one after my upgrade to Karmic (although I believe that was in the wrong board by mistake).

Now, I did a clean install of Karmic, and I've got everything up and running. I'm liking Karmic a lot so far, but there's one thing that's bugging me since I switched over from Windows: ATI's proprietary drivers. While I know this isn't specifically a Ubuntu thing, I would very much like to get them running with Compiz, etc. Right now, it's just not.


Here's what happens: when I enable the drivers (through the Administration>Hardware Drivers menu), the system won't load. I get the white Ubuntu after GRUB, then nothing but a blinking Caps Lock. Now, I've been looking into the problem, and I can't seem to figure out why.

My xorg.conf is very bare, all I have is this:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

I see no major errors in Xorg.0.log (attached below) as far as I can tell, although I think the lines stating "Cannot locate a core pointer/keyboard device." have something to do with the problem. I also get the following if I run "aticonfig --query-monitor"
```
aticonfig --query-monitor
Default Adapter - ATI Mobility Radeon HD 3400 Series
  Connected monitors: none
  Enabled monitors: none

```

And when I run fglrxinfo (or glxinfo, whatever that is), it returns:
```
fglrxinfo
Error: unable to open display (null)
```

I'm thinking this has got to be connected, right? Problem is, I've no idea how to fix it! I've been googling around, but all I find are people trying to get dual monitors and big desktop to work, which isn't my case. Could anyone, please, help me with this? Could it just be a case of specifying monitors/displays in xorg.conf? If so, where should I be looking for information on how to do this? Please, I could really use a hand here.

---

### Post by Lendro_Furioso on 2009-11-03
Oh, forgot to mention, it's an ATI Mobility Radeon HD 3470 on pretty much your standard laptop...

---

### Post by Lendro_Furioso on 2009-11-03
Still no takers, I see... Any chance some Ubuntu guru could take a look at this? Does anyone thing filing a bug report with ATI would help? I'm really starting to despair here, I've been at this for three days, and while I've learned some things, I'm still no closer to any sort of solution to the problem. Really, guys, I'd appreciate any sort of help here.

---

### Post by darksaga on 2009-11-03
dont know if u still have the problem(probably not)
I faced the same difficulty when i enabled fglrx. I dont think there is a stable way to work with fglrx, when u face such problems there's usually something wrong with the driver. 

Long story short in xorg.conf i changed "fglrx" to "ati" and everything works just fine!(except the effects of course)

---

### Post by Lendro_Furioso on 2009-11-03
> **darksaga said:**
> dont know if u still have the problem(probably not)
I faced the same difficulty when i enabled fglrx. I dont think there is a stable way to work with fglrx, when u face such problems there's usually something wrong with the driver. 

Long story short in xorg.conf i changed "fglrx" to "ati" and everything works just fine!(except the effects of course)

Yes, that's how I'm running it, but the point is you're not using the proprietary driver (which means no Compiz, ergo no desktop effects). I'm really stuck on this point, though, and some people are able to work with fglrx. What I'd like is at least to understand why this is happening, because I see no major errors in Xorg.log or syslogs in general.

Thanks for the reply.

---

### Post by draper7 on 2009-11-04
Have you tried disabling acpi?  From the grub boot menu select the kernel, hit "e", cursor down to where you see splash and type "acpi=off" (without quotes) after splash.

-d

---

### Post by swilleyman on 2009-11-04
I had very similar issues with an NVIDIA card.  I ran:


```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_blinking

sudo Xorg -configure
```

This generated a completely filled out configuration with hardware mappings and such.

I was able to boot into the desktop after this.

---

### Post by Lendro_Furioso on 2009-11-06
> **draper7 said:**
> Have you tried disabling acpi?  From the grub boot menu select the kernel, hit "e", cursor down to where you see splash and type "acpi=off" (without quotes) after splash.

-d

Thanks for the tip, but unfortunately this didn't work. The result was the same blinking Caps Lock and black screen.



> **swilleyman said:**
> I had very similar issues with an NVIDIA card.  I ran:


```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_blinking

sudo Xorg -configure
```

This generated a completely filled out configuration with hardware mappings and such.

I was able to boot into the desktop after this.

This seems like an interesting option, but unfortunately it's not working either. When I run it (in recovery mode, otherwise I get a message stating the X server is already running) it gives me a segmentation fault. Enclosed is the Xorg log from the event, which is the same thing I get on screen when using the command:

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux lendrofurioso-laptop 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=4e11c498-f2a2-49ca-a82b-56ee37d33bc9 ro single
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  6 21:56:28 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 2

(--) PCI:*(0:1:0:0) 1002:95c4:1179:ff1e ATI Technologies Inc Mobility Radeon HD 3400 Series rev 0, Mem @ 0xc0000000/268435456, 0xd6300000/65536, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
List of video drivers:
	sisusb
	ark
	ztv
	s3
	cirrus
	radeon
	openchrome
	siliconmotion
	voodoo
	r128
	tdfx
	i128
	intel
	v4l
	mach64
	ati
	chips
	mga
	apm
	nv
	s3virge
	fglrx
	rendition
	i740
	vmware
	tseng
	trident
	geode
	neomagic
	sis
	savage
	fbdev
	vesa
(II) LoadModule: "sisusb"
(II) Loading /usr/lib/xorg/modules/drivers//sisusb_drv.so
(II) Module sisusb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "ark"
(II) Loading /usr/lib/xorg/modules/drivers//ark_drv.so
(II) Module ark: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.7.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "ztv"
(II) Loading /usr/lib/xorg/modules/drivers//ztv_drv.so
(II) Module ztv: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 0.0.1
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "s3"
(II) Loading /usr/lib/xorg/modules/drivers//s3_drv.so
(II) Module s3: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 0.6.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "cirrus"
(II) Loading /usr/lib/xorg/modules/drivers//cirrus_drv.so
(II) Module cirrus: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.3.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.6.1.901, module version = 0.2.903
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "siliconmotion"
(II) Loading /usr/lib/xorg/modules/drivers//siliconmotion_drv.so
(II) Module siliconmotion: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.7.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "voodoo"
(II) Loading /usr/lib/xorg/modules/drivers//voodoo_drv.so
(II) Module voodoo: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 6.8.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "tdfx"
(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i128"
(II) Loading /usr/lib/xorg/modules/drivers//i128_drv.so
(II) Module i128: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.3.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "mach64"
(II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 6.8.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "chips"
(II) Loading /usr/lib/xorg/modules/drivers//chips_drv.so
(II) Module chips: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.4.11
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "apm"
(II) Loading /usr/lib/xorg/modules/drivers//apm_drv.so
(II) Module apm: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.1.14
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "s3virge"
(II) Loading /usr/lib/xorg/modules/drivers//s3virge_drv.so
(II) Module s3virge: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.10.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.66.10
	Module class: X.Org Video Driver
(II) LoadModule: "rendition"
(II) Loading /usr/lib/xorg/modules/drivers//rendition_drv.so
(II) Module rendition: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 4.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i740"
(II) Loading /usr/lib/xorg/modules/drivers//i740_drv.so
(II) Module i740: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vmware"
(II) Loading /usr/lib/xorg/modules/drivers//vmware_drv.so
(II) Module vmware: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 10.16.7
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "tseng"
(II) Loading /usr/lib/xorg/modules/drivers//tseng_drv.so
(II) Module tseng: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.3.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "geode"
(II) Loading /usr/lib/xorg/modules/drivers//geode_drv.so
(II) Module geode: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.11.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "neomagic"
(II) Loading /usr/lib/xorg/modules/drivers//neomagic_drv.so
(II) Module neomagic: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.2.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.10.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "savage"
(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for sisusb
(WW) Falling back to old probe method for ark
(WW) Falling back to old probe method for z4l
(II) z4l driver for Video4Linux
(WW) Falling back to old probe method for s3
(WW) Falling back to old probe method for cirrus
(II) Loading sub module "cirrus_laguna"
(II) LoadModule: "cirrus_laguna"
(II) Loading /usr/lib/xorg/modules/drivers//cirrus_laguna.so
(II) Module cirrus_laguna: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "cirrus_alpine"
(II) LoadModule: "cirrus_alpine"
(II) Loading /usr/lib/xorg/modules/drivers//cirrus_alpine.so
(II) Module cirrus_alpine: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
	ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI RS880
(WW) Falling back to old probe method for siliconmotion
(WW) Falling back to old probe method for voodoo
(WW) Falling back to old probe method for i128
(WW) Falling back to old probe method for v4l
(II) v4l driver for Video4Linux
(WW) Falling back to old probe method for apm
(WW) Falling back to old probe method for s3virge
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.66.10
(II) ATI Proprietary Linux Driver Release Identifier: 8.66.1                               
(II) ATI Proprietary Linux Driver Build Date: Sep  3 2009 21:35:19
(II) Loading PCS database from /etc/ati/amdpcsdb
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(**) ChipID override: 0x95C4
(**) Chipset Supported AMD Graphics Processor (0x95C4) found

Backtrace:
0: Xorg(xorg_backtrace+0x3b) [0x8133d6b]
1: Xorg(xf86SigHandler+0x55) [0x80c7d35]
2: [0xb7875400]
3: Xorg(xf86CallDriverProbe+0xde) [0x80aed5e]
4: Xorg(DoConfigure+0x1d0) [0x80b9ff0]
5: Xorg(InitOutput+0x176) [0x80b0246]
6: Xorg(main+0x1cb) [0x807234b]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xb7565b56]
8: Xorg [0x80719c1]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
```


What draws my attention here is the warning stating "(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found"

Now, this seems to be loading all available drivers, including radeon and fglrx. Could this be conflicting somehow? Maybe I will try uninstalling the radeon package, then running this. I'm also going to take a look at the documentation for this command, it seems to offer a few interesting options.


Thanks for the help so far!

---

### Post by Frila on 2009-11-09
Had the same problem. This helped me [http://ubuntuforums.org/showthread.php?t=1299188](http://ubuntuforums.org/showthread.php?t=1299188)
Maybe you have already tried it?

---

### Post by Lendro_Furioso on 2009-11-10
> **Frila said:**
> Had the same problem. This helped me [http://ubuntuforums.org/showthread.php?t=1299188](http://ubuntuforums.org/showthread.php?t=1299188)
Maybe you have already tried it?

I've tried it, unfortunately, same results... I've been digging into this in my dwindling amount of free time, and still haven't found any leads. What really strikes me as odd is the fact that no major errors pop up in the logs. I also tried disabling acpi in the bootloader as draper7 suggested here, with no results.
I'm convinced this has something to do with the fact that fglrxinfo returns an error ("unable to open display"). I haven't found anyone with the same problem concerning a single-monitor setup, though...

Thank you very much for the suggestion, I appreciate the time you took to answer.

---

### Post by Frila on 2009-11-10
Well, my problems are not solved fully because it seems be instable. Often when I start up I get this black screen and blinking Caps Lock. But after a restart it starts up fine :confused:
Ubuntu 9.04 works great so maybe I have to stick to that. :sad: or go back to Fedora...

---

### Post by markbuntu on 2009-11-10
You could try adding the BusID in xorg.conf like this which is from my xorg.conf:

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

That should only be needed where there is more than one gpu but that may have changed. 

sudo aticonfig --initial -f 

should write that in xorg.conf for you. You need the sudo to run it as root and the -f flag forces an overwrite of the existing xorg.conf which is renamed and saved. You could try doing that again, it should do no harm. 

You could also look in your kern.log and see if there are any strange messages about the PCI bus or ACPI etc.

---

### Post by Rafaelcrocha on 2009-11-17
Hi,

I am getting the same problem in toishiba a305, video hd3470... I think this is an old bug

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/285701](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/285701)

Any news? I am getting this since karmic alpha...

---

### Post by rkdwv on 2009-11-18
```
aticonfig --initial
aticonfig --acpi-servces=off
```

That helped me in recovery mode on Toshiba Satellite A300D-20A

---

### Post by brakbox on 2009-11-22
```
aticonfig --initial -f
aticonfig --acpi-services=off
```

solved the blackscreenissues on my HP EliteBook 8730w (ATI Mobility Radeon HD 3670)

---

### Post by manishsk on 2009-11-23
I am facing the same issue. Toshiba A305D AMD Readeon HD3650.

Not been able to solve this. After doing several reinstall I installed the drivers which are available on AMD's website. Search ofr linux drivers of your card. I am able enjoy the effects but they are not as fast as 9.04 i think.

Also I get a blank screen still but once I restart the laptop again it works again. Due to this I am not really happy with 9.10.

Ubuntu should realease a fix update for this soon. Please...

---

### Post by Yellow Pasque on 2009-11-23
There's also the possibility of using open-source drivers and the xorg-edgers PPA to get 3D acceleration working with those drivers: [http://ubuntuforums.org/showpost.php?p=8340519&postcount=12](http://ubuntuforums.org/showpost.php?p=8340519&postcount=12)

---

### Post by harmony on 2009-11-23
> **Temüjin said:**
> There's also the possibility of using open-source drivers and the xorg-edgers PPA to get 3D acceleration working with those drivers: [http://ubuntuforums.org/showpost.php?p=8340519&postcount=12](http://ubuntuforums.org/showpost.php?p=8340519&postcount=12)


I've tried the amd drivers, the proprietary drivers, and the radeonhd drivers with a 4850, Im having no luck only a black screen.I will try those open-source drivers, and xorg-edgers sometime.[-o<

---

### Post by Lendro_Furioso on 2009-11-24
I haven't had any luck solving this with Catalyst 9.10. While markbuntu's suggestion of "sudo aticonfig --initial -f" does give me a more detailed xorg.conf with BusID's, etc, the problem persists. As mentioned earlier, under Catalystr 9.10 turning off acpi did nothing to help.

Today I finally had time to sit down and try this with Catalyst 9.11. While it didn't work, the problem seems different now... The system still becomes unresponsive at the same point (right after the white Ubuntu symbol disappears) but Caps Lock no longer blinks, and I can reboot with Alt+PrintScreen key combos. So while that's an improvement of sorts, it still doesn't work. The system hangs indefinitely, with periodical access to HD (as witnessed by the blinking LED light). Now, looking at syslog, this is what I get:

```
kernel: [   26.412803] fglrx_pci 0000:01:00.0: irq 31 for MSI/MSI-X
kernel: [   26.413438] [fglrx] Firegl kernel thread PID: 1532
anacron[1547]: Anacron 2.3 started on 2009-11-23
anacron[1547]: Normal exit (0 jobs run)
kernel: [   26.696948] CPU0 attaching NULL sched-domain.
kernel: [   26.696952] CPU1 attaching NULL sched-domain.
kernel: [   26.708587] CPU0 attaching sched-domain:
kernel: [   26.708590]  domain 0: span 0-1 level MC
kernel: [   26.708594]   groups: 0 1
kernel: [   26.708599] CPU1 attaching sched-domain:
kernel: [   26.708602]  domain 0: span 0-1 level MC
kernel: [   26.708605]   groups: 1 0
kernel: [   27.112846] ------------[ cut here ]------------
kernel: [   27.112851] kernel BUG at /build/buildd/linux-2.6.31/mm/slub.c:2929!
kernel: [   27.112854] invalid opcode: 0000 [#1] SMP
kernel: [   27.112857] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill0/state
kernel: [   27.112859] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec arc4 ecb $
kernel: [   27.112895]
kernel: [   27.112899] Pid: 1371, comm: Xorg Tainted: P           (2.6.31-14-generic-pae #48-Ubuntu) Satellite A300
kernel: [   27.112902] EIP: 0060:[<c01e2c82>] EFLAGS: 00013246 CPU: 0
kernel: [   27.112907] EIP is at kfree+0xe2/0xf0
kernel: [   27.112909] EAX: 80000400 EBX: bfe27540 ECX: f55c81e0 EDX: c30014e0
kernel: [   27.112911] ESI: f87ac00b EDI: f55a9800 EBP: f54c1e64 ESP: f54c1e50
kernel: [   27.112913]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
kernel: [   27.112916] Process Xorg (pid: 1371, ti=f54c0000 task=f55d3ed0 task.ti=f54c0000)
kernel: [   27.112918] Stack:
kernel: [   27.112919]  f55c81e0 4131c938 f55c8120 00000002 f55a9800 f54c1e6c f87ac00b 00000001
kernel: [   27.112924] <0> f87e583d bfe27540 f54c1e94 00000004 f50f0f0c f54c1ec0 00000000 bfe27540
kernel: [   27.112930] <0> f5890000 00000040 00000001 46495441 00000002 f55c8100 00000000 bfe27540
kernel: [   27.112937] Call Trace:
kernel: [   27.112978]  [<f87ac00b>] ? KCL_MEM_SmallBufferFree+0xb/0x10 [fglrx]
kernel: [   27.113021]  [<f87e583d>] ? firegl_acpi_eval_method+0x19d/0x390 [fglrx]
kernel: [   27.113025]  [<c0150a20>] ? capable+0x10/0x40
kernel: [   27.113067]  [<f87e56a0>] ? firegl_acpi_eval_method+0x0/0x390 [fglrx]
kernel: [   27.113071]  [<c040647d>] ? ppp_unregister_channel+0x7d/0xf0
kernel: [   27.113108]  [<f87bb3bd>] ? firegl_ioctl+0x22d/0x2b0 [fglrx]
kernel: [   27.113111]  [<c040647d>] ? ppp_unregister_channel+0x7d/0xf0
kernel: [   27.113117]  [<c040647d>] ? ppp_unregister_channel+0x7d/0xf0
kernel: [   27.113149]  [<f87b09b9>] ? ip_firegl_ioctl+0x19/0x20 [fglrx]
kernel: [   27.113153]  [<c040647d>] ? ppp_unregister_channel+0x7d/0xf0
kernel: [   27.113156]  [<c01f84c3>] ? vfs_ioctl+0x73/0x90
kernel: [   27.113159]  [<c040647d>] ? ppp_unregister_channel+0x7d/0xf0
kernel: [   27.113162]  [<c01f8791>] ? do_vfs_ioctl+0x71/0x310
kernel: [   27.113167]  [<c0578b0b>] ? do_page_fault+0x19b/0x380
kernel: [   27.113170]  [<c01f8a8f>] ? sys_ioctl+0x5f/0x80
kernel: [   27.113173]  [<c0103283>] ? sysenter_do_call+0x12/0x28
kernel: [   27.113176]  [<c040647d>] ? ppp_unregister_channel+0x7d/0xf0
kernel: [   27.113178] Code: 8b 52 0c 8b 02 eb 81 8b 3d c8 f5 78 c0 85 ff 0f 84 55 ff ff ff 8b 0f 83 c7 04 89 da 89 f0 ff d1 8b 0f 85 c9 75 f$
kernel: [   27.113213] EIP: [<c01e2c82>] kfree+0xe2/0xf0 SS:ESP 0068:f54c1e50
kernel: [   27.113219] ---[ end trace 6ebbf340108b04e8 ]---
kernel: [   27.113765] [fglrx:firegl_release] *ERROR* device busy: 1 0
kernel: [   27.113767] [fglrx] release failed with code -EBUSY
acpid: client 1371[0:0] has disconnected
acpid: client connected from 1585[0:0]
gdm-binary[1283]: WARNING: GdmDisplay: display lasted 0.563376 seconds
kernel: [   27.756935] ------------[ cut here ]------------
kernel: [   27.756939] kernel BUG at /build/buildd/linux-2.6.31/mm/slub.c:2929!
kernel: [   27.756942] invalid opcode: 0000 [#2] SMP
kernel: [   27.756945] last sysfs file: /sys/module/fglrx/initstate
kernel: [   27.756947] Modules linked in: binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec arc4 ecb $
kernel: [   27.756981]
kernel: [   27.756984] Pid: 1585, comm: Xorg Tainted: P      D    (2.6.31-14-generic-pae #48-Ubuntu) Satellite A300
kernel: [   27.756987] EIP: 0060:[<c01e2c82>] EFLAGS: 00013246 CPU: 0
kernel: [   27.756992] EIP is at kfree+0xe2/0xf0
kernel: [   27.756993] EAX: 80000400 EBX: bfadb160 ECX: f45acfc0 EDX: c2ffab60
kernel: [   27.756995] ESI: f87ac00b EDI: f55a9500 EBP: f5403e64 ESP: f5403e50
kernel: [   27.756997]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
kernel: [   27.757000] Process Xorg (pid: 1585, ti=f5402000 task=f5ea3ed0 task.ti=f5402000)

```

After which he just loops this indefinitely, until I reboot with Alt+PrintScreen key combos. The periodiral HD access are the logs, I presume. Should I report this as a bug?

---

### Post by Lendro_Furioso on 2009-11-24
Update: I tried the "aticonfig --acpi-services=off" option with this new setup, and it actually booted, but the results were less than satisfactory. The system is incredibly slow, even simple things like scrolling in Firefox. Video playback was, of course, choppy. I'm also unable to enable desktop effects, though fglrx does seem to be in use, as witnessed by the Hardware Drivers option in System>Administration and lshw, which returns the following:

```
(...)
           *-display
                description: VGA compatible controller
                product: Mobility Radeon HD 3400 Series
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: **driver=fglrx_pci** latency=0
                resources: irq:31 memory:c0000000-cfffffff(prefetchable) ioport:5000(size=256) memory:d6300000-d630ffff memory:d6320000-d633ffff(prefetchable)
(...)

```
(emphasis mine)


I also get the same errors running "Xorg -configure" and even simple stuff like "fglrxinfo". I'm doubtful this is just a case of tweaking xorg.conf to get it to work better. Any suggestions? Honestly, I'm fresh out of ideas...

I may give the open source drivers a go again, though they've failed me in the past. If that doesn't work, I'll try Temüjin's xorg-edgers suggestion.

---

### Post by biker3 on 2009-11-25
I have the same error with Gigabyte HD 4650 AGP 1 GB with fglrx:mad:
And if I try with radeonhd I obtain
> (II) RADEONHD: version 1.2.5, built from non-git sources

(II) Primary Device is: PCI 01@00:00:0
(EE) No devices detected.

Fatal server error:
no screens found

---

### Post by markbuntu on 2009-11-26
> **Lendro_Furioso said:**
> Update: I tried the "aticonfig --acpi-services=off" option with this new setup, and it actually booted, but the results were less than satisfactory. The system is incredibly slow, even simple things like scrolling in Firefox. Video playback was, of course, choppy. I'm also unable to enable desktop effects, though fglrx does seem to be in use, as witnessed by the Hardware Drivers option in System>Administration and lshw, which returns the following:

```
(...)
           *-display
                description: VGA compatible controller
                product: Mobility Radeon HD 3400 Series
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: **driver=fglrx_pci** latency=0
                resources: irq:31 memory:c0000000-cfffffff(prefetchable) ioport:5000(size=256) memory:d6300000-d630ffff memory:d6320000-d633ffff(prefetchable)
(...)

```
(emphasis mine)


I also get the same errors running "Xorg -configure" and even simple stuff like "fglrxinfo". I'm doubtful this is just a case of tweaking xorg.conf to get it to work better. Any suggestions? Honestly, I'm fresh out of ideas...

I may give the open source drivers a go again, though they've failed me in the past. If that doesn't work, I'll try Temüjin's xorg-edgers suggestion.

Slow performance is sometimes an indication that DRM is not working which is the result of no kernel modules. You should look in the Xorg.0.log to see what is going on. (EE) messages are most important.

---

### Post by manishsk on 2009-11-30
Guys

Please check below post. I am able to solve the similar problem with this post. acpi-services=off is actully required. I do not experience slow performance as mentioned above. 

There can be some different reason...

I hope it helps. My suggestion is use the drivers on AMD/ATI site.

[http://ubuntuforums.org/showthread.php?t=1315199]("http://ubuntuforums.org/showthread.php?t=1315199")

Thanks.

---

### Post by Lendro_Furioso on 2009-12-01
Major update! I'm not sure what it was, but the latest ubuntu updates seem to have done the trick. I re-installed fglrx, and I've got desktop effects working, although with acpi off. I'm marking this thread as solved.

I still need to apply the backfill patch to get rid of the delay in window maximization, but it all appears to be in good shape for now. 


I'd like to extend a big thank you to everyone who helped me, and kept the thread alive. This is why the ubuntu community is so great.

---

### Post by manishsk on 2009-12-02
Hi Lendro_Furioso 

You Installed the driver from the "Hardware Drivers" section which says tested by Ubuntu developers or from the AMD/ATI driver site?

Thanks,
Manish

---

### Post by Lendro_Furioso on 2009-12-02
> **manishsk said:**
> Hi Lendro_Furioso 

You Installed the driver from the "Hardware Drivers" section which says tested by Ubuntu developers or from the AMD/ATI driver site?

Thanks,
Manish

Initially from the "Hardware Drivers" section, since Karmic has Catalyst 9.10 in the repositories. I now have it working with Catalyst 9.11 (so, the latest version, from November, which came out in the mean time) from the ATI website. I built the .debs and installed them manually, then ran "sudo aticonfig --initial -f" for a pre-configured xorg.conf. There's a pretty complete guide here: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

It will only work without acpi, so "aticonfig -acpi-services=off" is required. Not optimal, but at least it's up and running. I'll probably keep this version of catalyst buried in the hard drive and keep trying newer versions as they come out to see if it gets better.

Hope it helps!

---

### Post by manishsk on 2009-12-03
Yeah I did install 9.11 from the AMD site. It works good enough. I did not build the .debs. I installed as it is. Sa far working fine.

But now facing a different problem. This thread is not for that problem but related to it. Its because of the recent updates from ubuntu.

**Check the details here if you get some time:**
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/491483")

---

### Post by YayForOpenSource on 2010-03-27
aticonfig --initial -f
aticonfig --acpi-services=off

Work for me on my Toshiba M200. Thank you.

---

### Post by Sepiraph on 2010-04-25
In case the above doesn't solve the issue (as in my case), follow this:

> [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---


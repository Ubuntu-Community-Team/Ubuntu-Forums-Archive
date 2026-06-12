---
title: "how do i force agp rate to 4x?"
date: 2006-07-22
forum: Multimedia &amp; Video
---

### Post by tofudrifter on 2006-07-22
I have a radeon 9800 on a motherboard with amd-8151 agp chipset.  i can load fglrx fine but as soon as i run a 3d app the system will hard lock, ie glxgears will start and then everything will freeze.

same thing happens in windows and i found the only way to stop this is to set agp rate to 4x. any ideas on how i would do this in linux?

---

### Post by whatever on 2006-07-22
are you sure you are using the fglrx driver? the problem you describe sound very much like a known bug in the open source r300 dri...

lets assume it is a fglrx problem,
did you have a look in your bios settings? on my nforce2 there is an option to en-/disable agp 8x.
otherwise you might get help in this forum: [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88)

---

### Post by tofudrifter on 2006-07-22
yes i'm pretty sure i am using fglrx

dmesg | grep fglrx
```

[   59.808652] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   59.810507] [fglrx] Maximum main memory to use for locked dma buffers: 1885 MBytes.
[   59.810654] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[   61.036886] [fglrx] AGP GART is configured for kernel IOMMU, internal GART will not be used
[   61.037039] [fglrx] AGP detected, AgpState   = 0x1f000b3b (hardware caps of chipset)
[   61.038029] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[   61.045518] [fglrx] total      GART = 134217728
[   61.045547] [fglrx] free       GART = 118222848
[   61.045550] [fglrx] max single GART = 118222848
[   61.045572] [fglrx] total      LFB  = 126873600
[   61.045579] [fglrx] free       LFB  = 116387840
[   61.045601] [fglrx] max single LFB  = 116387840
[   61.045648] [fglrx] total      Inv  = 134217728
[   61.045692] [fglrx] free       Inv  = 134217728
[   61.045703] [fglrx] max single Inv  = 134217728
[   61.045720] [fglrx] total      TIM  = 0

```

lsmod | grep fglrx
```
fglrx                 451892  8

```

and my xorg.conf has
```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NJ [Radeon 9800 XT]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection
```

changing bios setting to disable agp 8x causes machine to not even post.
the amd-8151 is known to have problems with radeon cards
the way to fix in windows is to set agp to 4x in ati's windows util but i'm having trouble finding a way to do this in linux/ubuntu

---

### Post by autocrosser on 2006-07-22
First--open a terminal & "man radeon" (without the quotes--)

Second--in your "Device" section (xorg.conf---/etc/X11/xorg.conf)

Section "Device"
    Identifier    "ATI Technologies, Inc. RV280"
    Driver        "radeon"
    BusID        "PCI:1:0:0"
         Option          "MergedFB"              "true"
        Option          "MergedDPI"             "100 100"
        Option          "MergedNonRectangular"  "true"
        Option          "CRT2Position"          "RightOf"
        Option          "MetaModes"             "1280x1024-1280x1024 1024x768-1024x768 1024x768-800x600 800x600-800x600"
        #Option          "DynamicClocks"         "true"
        Option          "AGPMode"                "4"
        Option          "AGPFastWrite"           "true"
        #Option          "EnableDepthMoves"       "true"
        Option          "EnablePageFlip"          "true"
        Option          "DDCMode"                 "true"
        Option          "Backingstore"          "true"
        Option          "AccelMethod"           "EXA"  
        #Option          "AllowGLXWithComposite" "true"
        Option          "SubPixelOrder"         "NONE"
        Option          "ColorTiling"           "false"
        Option          "FBTexPercent"          "30"
EndSection

I know not all of these will work with your card--take a look at the man page & decide if some or all make it work for you---(this file was for dual monitors & without the "restricted driver")--the man page will at least "point" you the right way.

You might also take a look at your System log (Xorg.0.log) & see what is loading--

---

### Post by tofudrifter on 2006-07-22
i'm using the fglrx driver so the agpmode option was ignored.
i think what i have to do is disable agpgart in kernel,
use Option "UseInternalAGPGART" "yes" in xorg.conf and then find a way to set agpmode to 4x
or
is there a way to set agpgart in kernel to 4x?

---


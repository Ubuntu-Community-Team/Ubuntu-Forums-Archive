---
title: "Unable to get DRI on ati 8500"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by Heretic09 on 2006-06-02
I have an ati 8500 agp card, the new ati drivers don't work at all with r200 models so i'm resorting to using the radeon driver. The problem is even though I have the following in xorg.conf:

```
...
Section "Module"
  Load "dri"
  Load "glx"
  ...
EndSection
...
Section "Device"
  Driver "radeon"
  ...
EndSection
...
Section "dri"
  Mode 0666
EndSection
```

Glx info still shows

```
direct rendering: No
```

the xorg log shows nothing is amiss. Any ideas why dri is not being enabled?

---

### Post by barney_1 on 2006-06-02
I also am having trouble with DRI.  From my Xorg.0.log:
```
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

I'll post the whole file if anyone feels like looking.  Sure would be nice to use the hardware I paid top dollar for. ;)

---

### Post by Game_Ender on 2006-06-04
I have basically the same log file as you do.  With the exact same error message:
```
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

This means the fglrx module is not loaded so you will not get any 3D hardware acceleration.  Now I checked on my computer and there are no "card" devices in the /dev/dri/ directory (which is why the module can't find them).  I am currently trying to figure out why this is so.

EDIT: More info: "LIBGL_DEBUG=verbose glxinfo" shows this:```

name of display: :0.0
libGL error: XF86DRIQueryDirectRenderingCapable returned false
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0  screen: 0
```
The instructions I used to install my drivers are these ones from the [wiki]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29").

---

### Post by joshuas on 2006-08-03
Hi,

Anyone solved this pblm ?

I have exactly the same pblm :

Xorg.0.log

```

(II) fglrx(0): detected X.org 7.0.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x03fe0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)

```

```

$lspci -v
0000:01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
        Subsystem: Universal Scientific Ind.: Unknown device 0380
        Flags: bus master, fast devsel, latency 0
        Memory at dc010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #10 [0001]

```

my xorg.conf :

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Module"    

        #Load  "GLcore"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc" 
        Load  "dri" 
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        #ChipId      0x5b70
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "UseInternalAGPGART" "no"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

I'm running Dapper, a custom kernel 2.6.17.7 and ati-driver-installer-8.27.10-x86.run compiled as [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").

running fglrxinfo :
```
$ fglrxinfo 
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
Error: unable to open display :0

```

Any ideas ???

tx

---

### Post by Pest_789 on 2006-10-20
I just ran into this problem too.  I did solve it though.  

I'd seen this sort of thing happen before with nVidia drivers.  

In this case I needed to uninstall the fgrlx drivers that snuck into my system with the 'linux-restricted-modules' packages.  Even though that version of fgrlx wasn't being used, it was preventing the copy I downloaded from ATI from installing it's kernel module.  

Once I had all my linux-restricted-modules packages removed, I just re-installed the one I downloaded from ATI (with X stopped) and restarted X and everything worked great.

---


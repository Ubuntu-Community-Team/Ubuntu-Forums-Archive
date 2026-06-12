---
title: "no compiz/3d graphics in 10.10 with nouveau"
date: 2010-10-18
forum: Multimedia Software
---

### Post by roberto.tomas on 2010-10-18
All 3d applications run with a solid black screen, and compiz will try to revert to the fallback wm, even though I have the new nouveau/gallium setup in 10.10.

glxgears appears to *think* it has a working screen, but it stays blank:
```
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
3570 frames in 5.0 seconds = 713.841 FPS
3298 frames in 5.0 seconds = 659.541 FPS
3599 frames in 5.0 seconds = 719.699 FPS
3592 frames in 5.0 seconds = 718.265 FPS
3625 frames in 5.0 seconds = 724.964 FPS
```I have the neaveau drivers and I think everything is set up properly:

glxinfo | grep direct:
```
direct rendering: Yes:
```glxinfo | grep -i opengl:
```
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NV43
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
```wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check && chmod it &&
compiz-check:
```
$ ./compiz-check
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   Xfce
 Graphics chip:         nVidia Corporation NV43 [GeForce 6600] (rev a2)
 Driver in use:         nouveau
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on the whitelist. 

Would you like to know more? (Y/n) Y

 Your driver is not widely known to work with Compiz and thus may be
 blacklisted on certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) y
```xorg.conf:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "ServerFlags"
    Option       "AIGLX" "on"
    Option       "GlxVisuals" "all"
EndSection

Section "DRI"
    mode 0666
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "dri"
    Load  "extmod"
    Load  "dbe"
    Load  "glx"
    Load  "dri2"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    ##Driver      "nv"
    Driver      "nouveau"
    BusID       "PCI:10:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```uname -r
```
2.6.35-22-powerpc64-smp
```the only thing that worries me is some of dmesg:
```
[    7.161180] [drm] nouveau 0000:0a:00.0: Detected an NV40 generation card (0x043100a4)
[    7.161188] checking generic (90020000 3e8000) vs hw (90000000 10000000)
[    7.161191] fb: conflicting fb hw usage nouveaufb vs OFfb NVDA,Displ - removing generic driver
[    7.161222] Console: switching to colour dummy device 80x25
[    7.161722] Trying to free nonexistent resource <0000000090020000-0000000090407fff>
[    7.162086] [drm] nouveau 0000:0a:00.0: OF bios successfully copied (6447 bytes)
[    7.162146] [drm] nouveau 0000:0a:00.0: Attempting to load BIOS image from PRAMIN
...
[    7.222329] [drm] nouveau 0000:0a:00.0: ... BIOS checksum invalid
[    7.222332] [drm] nouveau 0000:0a:00.0: Attempting to load BIOS image from PROM
[    7.222373] [drm] nouveau 0000:0a:00.0: ... BIOS signature not found
[    7.222377] [drm] nouveau 0000:0a:00.0: Attempting to load BIOS image from PCIROM
[    7.222434] [drm] nouveau 0000:0a:00.0: ... BIOS signature not found
[    7.222437] [drm] nouveau 0000:0a:00.0: Attempting to load BIOS image from ACPI
[    7.222440] [drm] nouveau 0000:0a:00.0: ... BIOS signature not found
[    7.222443] [drm] nouveau 0000:0a:00.0: Using BIOS image from PRAMIN
[    7.243132] firewire_ohci: Added fw-ohci device 0001:03:0e.0, OHCI v1.0, 8 IR + 8 IT contexts, quirks 0x0
[    7.282048] [drm] nouveau 0000:0a:00.0: BIT BIOS found
[    7.282052] [drm] nouveau 0000:0a:00.0: Bios version 05.43.02.75
[    7.282057] [drm] nouveau 0000:0a:00.0: BIT table 'd' not found
[    7.282064] [drm] nouveau 0000:0a:00.0: Found Display Configuration Block version 3.0
[    7.282071] [drm] nouveau 0000:0a:00.0: Raw DCB entry 0: 01000100 00000028
[    7.282079] [drm] nouveau 0000:0a:00.0: Raw DCB entry 1: 03000102 00000000
[    7.282082] [drm] nouveau 0000:0a:00.0: Raw DCB entry 2: 04011210 00000028
[    7.282085] [drm] nouveau 0000:0a:00.0: Raw DCB entry 3: 02111212 02000100
[    7.282088] [drm] nouveau 0000:0a:00.0: Raw DCB entry 4: 02011211 0020c070
[    7.282088] [drm] nouveau 0000:0a:00.0: Raw DCB entry 4: 02011211 0020c070
[    7.282093] [drm] nouveau 0000:0a:00.0: DCB connector table: VHER 0x30 5 7 2
[    7.282097] [drm] nouveau 0000:0a:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[    7.282100] [drm] nouveau 0000:0a:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[    7.282132] [drm] nouveau 0000:0a:00.0: Parsing VBIOS init table 0 at offset 0x0744
[    7.282402] [drm] nouveau 0000:0a:00.0: Parsing VBIOS init table 1 at offset 0x0B87
[    7.327084] [drm] nouveau 0000:0a:00.0: Parsing VBIOS init table 2 at offset 0x105B
[    7.327111] [drm] nouveau 0000:0a:00.0: Parsing VBIOS init table 3 at offset 0x1195
[    7.350753] [drm] nouveau 0000:0a:00.0: Parsing VBIOS init table 4 at offset 0x1273
[    7.350766] [drm] nouveau 0000:0a:00.0: Detected 256MiB VRAM
[    7.385940] [TTM] Zone  kernel: Available graphics memory: 1491700 kiB.
[    7.385943] [TTM] Initializing pool allocator.
[    7.390687] [drm] nouveau 0000:0a:00.0: 64 MiB GART (aperture)
[    7.391021] [drm] nouveau 0000:0a:00.0: Allocating FIFO number 0
[    7.393789] [drm] nouveau 0000:0a:00.0: nouveau_channel_alloc: initialised FIFO 0
[    7.393806] [drm] nouveau 0000:0a:00.0: Initial CRTC_OWNER is 0
[    7.393923] [drm] nouveau 0000:0a:00.0: Detected a DVI-I connector
[    7.394094] [drm] nouveau 0000:0a:00.0: Detected a DVI-I connector
[    7.394193] [drm] nouveau 0000:0a:00.0: Detected a TV connector
[    7.395960] [drm] nouveau 0000:0a:00.0: Setting dpms mode 3 on vga encoder (output 0)
[    7.395969] [drm] nouveau 0000:0a:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[    7.395974] [drm] nouveau 0000:0a:00.0: Setting dpms mode 3 on vga encoder (output 2)
[    7.395978] [drm] nouveau 0000:0a:00.0: Setting dpms mode 3 on tmds encoder (output 3)
[    7.395982] [drm] nouveau 0000:0a:00.0: Setting dpms mode 3 on TV encoder (output 4)
[    7.710318] [drm] nouveau 0000:0a:00.0: allocated 2560x1600 fb: 0x49000, bo c000000002315c00
[    7.721176] [drm] nouveau 0000:0a:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[    7.721186] [drm] nouveau 0000:0a:00.0: 0x147A: Parsing digital output script table
[    7.734275] firewire_core: created device fw0: GUID 001451fffe1b51d4, S800
[    7.815626] [drm] nouveau 0000:0a:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[    7.815631] [drm] nouveau 0000:0a:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[    7.815652] Console: switching to colour frame buffer device 320x100
[    7.818965] fb0: nouveaufb frame buffer device
[    7.818968] drm: registered panic notifier
[    7.818973] Slow work thread pool: Starting up
[    7.819143] Slow work thread pool: Ready
[    7.819152] [drm] Initialized nouveau 0.0.16 20090420 for 0000:0a:00.0 on minor 0
```

---

### Post by roberto.tomas on 2010-11-05
bump

---

### Post by cgb on 2010-11-05
Have you tried installing the NVIDIA driver and disabling nouveau?  This would most likely correct any video issues..

---

### Post by roberto.tomas on 2010-11-05
> **cgb said:**
> Have you tried installing the NVIDIA driver and disabling nouveau?  This would most likely correct any video issues..

no, I can't use the nvidia drivers. I am stuck with nouveau, but it is reported as working.

---

### Post by cgb on 2010-11-05
Hmm...  Possibly related to the same issues in this thread..  Might be worth a shot..

[http://ubuntuforums.org/showthread.php?t=210439]("http://ubuntuforums.org/showthread.php?t=210439")

---

### Post by roberto.tomas on 2010-11-06
> **cgb said:**
> Hmm...  Possibly related to the same issues in this thread..  Might be worth a shot..

[http://ubuntuforums.org/showthread.php?t=210439](http://ubuntuforums.org/showthread.php?t=210439)

umm, thank you ...

that thread is also someone using the nvidia driver. I'm not using that, I'm using the open-source nouveau driver that was released ready to work with compiz in 10.10

---

### Post by mc4man on 2010-11-06
You can install libgl1-mesa-dri-experimental  - fairly safe, older build or use the xorg-edgers fresh X crack ppa - new builds, may work better, may break at any moment
(the ppa needs to used as a whole, not individual packages, having ppa-purge installed/knowing how to use is a must

---

### Post by roberto.tomas on 2010-11-08
thanks mc4man
> **mc4man said:**
> You can install libgl1-mesa-dri-experimental  - fairly safe, older build or use the xorg-edgers fresh X crack ppa - new builds, may work better, may break at any moment
(the ppa needs to used as a whole, not individual packages, having ppa-purge installed/knowing how to use is a must

I have the older one -- it has some green pixel noise every once in a while but otherwise it works in non-3d just fine. Looking into my problem further I think I found a symptom that points to that package.

```
$ glxinfo|grep renderer
OpenGL renderer string: Gallium 0.4 on NV43
```I believe that is supposed to say "nouveau/NV43" for 3D rendering.

```
$ sudo apt-cache show libgl1-mesa-dri-experimental
Package: libgl1-mesa-dri-experimental
Priority: optional
Section: universe/libs
Installed-Size: 7252
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: powerpc
Source: mesa
Version: 7.9~git20100924-0ubuntu2
Depends: libc6 (>= 2.4), libdrm-nouveau1 (>= 2.4.20-3~), libdrm2 (>= 2.3.1), libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.2.1), libstdc++6 (>= 4.1.1), libtalloc2 (>= 2.0.0)
Filename: pool/universe/m/mesa/libgl1-mesa-dri-experimental_7.9~git20100924-0ubuntu2_powerpc.deb
Size: 990504
MD5sum: 300b0489d073b519a7d0a0c3ee088f03
SHA1: fb092029d6c521d0a00eb3ef9e491ca8850f9b87
SHA256: bc6fb3b306f2921edc0b318a27b81cbe29987458af5983633afc44438bfd0111
Description: A free implementation of the OpenGL API -- Extra DRI modules
 This version of Mesa provides GLX and DRI capabilities: it is capable of
 both direct and indirect rendering.  For direct rendering, it can use DRI
 modules from the libgl1-mesa-dri package to accelerate drawing.
 .
 This package does not include the OpenGL library itself, only the DRI
 modules for accelerating direct and indirect rendering.  The drivers
 in this package may provide more features than the drivers in the
 libgl1-mesa-dri at the cost of less stability.
 .
 For a complete description of Mesa, please look at the
 libgl1-mesa-swx11 package.
Homepage: http://mesa3d.sourceforge.net/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```Am I missing something to attach this library to the gallium driver?

---

### Post by cgb on 2010-11-08
> umm, thank you ...

that thread is also someone using the nvidia driver. I'm not using that, I'm using the open-source nouveau driver that was released ready to work with compiz in 10.10 

Sorry I realized you were not using the NVIDIA drivers but I thought it still might be worth taking a look at that thread since it was related to your same card and possible firmware issues with it and how it reports.  

```
$ glxinfo|grep renderer
OpenGL renderer string: Gallium 0.4 on NV43
```

Gallium, if I'm not mistaken, is the 3d driver for Nouveau so I don't think there is anything out of order here.  Unfortunately not seeing much else to help with. Hopefully someone else can assist further..

---

### Post by roberto.tomas on 2010-11-10
> **cgb said:**
> ```
$ glxinfo|grep renderer
OpenGL renderer string: Gallium 0.4 on NV43
```Gallium, if I'm not mistaken, is the 3d driver for Nouveau so I don't think there is anything out of order here.

Yea, I'm a little ood here too. I *think* Gallium is the 3d extension for the nouveau driver, which is supposed to interface the mesa opengl libraries to the driver for the video card. But notice that the OpenGL renderer string says gallium is set to bind to the **nv **driver, and I don't see nouveau there. That could be a problem, no?

---

### Post by mc4man on 2010-11-10
If you're getting direct rendering (which it appears you are) then there is nothing wrong.
the nv43 is the 'description' of the adapter (card), not the driver, nv means nvidia, not nv driver

---


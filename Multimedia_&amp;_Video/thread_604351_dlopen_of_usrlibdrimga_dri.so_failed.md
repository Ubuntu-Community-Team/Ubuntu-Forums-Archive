---
title: "dlopen of /usr/lib/dri/mga_dri.so failed"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by mpfleger on 2007-11-06
Hi all.

Running Xubuntu 7.10 on older PIII box with Matrox G400. Had DRI working on this card in Xubuntu 6.06 LTS as was reported in glxinfo Running glxinfo in new install reports DRI not working, a finding which is supported by 3D application (lack of) performance.

My apologies in advance if this has already been answered. My searches pulled up nothing relevant, though I might have forgotten to check something =/

The relevant parts of xorg.conf:

```

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

...

Section "Device"
        Identifier      "Matrox Graphics, Inc. MGA G400/G450"
        Driver          "mga"
        BusID           "PCI:1:0:0"
        Option          "OldDmaInit"            "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Matrox Graphics, Inc. MGA G400/G450"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```


Relevant parts of /var/log/Xorg.0.log:

```

(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI

...

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX

...

(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.4.6
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.2

...

(II) MGA(0): [drm] bpp: 32 depth: 24
(II) MGA(0): [drm] Sarea 2200+664: 2864
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) MGA(0): [drm] loaded kernel module for "mga" driver
(II) MGA(0): [drm] DRM interface version 1.3
(II) MGA(0): [drm] created "mga" driver at busid "pci:0000:01:00.0"
(II) MGA(0): [drm] added 8192 byte SAREA at 0xe0b3b000
(II) MGA(0): [drm] mapped SAREA 0xe0b3b000 to 0xb628b000
(II) MGA(0): [drm] framebuffer handle = 0xe8000000
(II) MGA(0): [drm] added 1 reserved context for kernel
(II) MGA(0): [agp] Mode 0x1f000201 [AGP 0x8086/0x7190; Card 0x102b/0x0525]
(II) MGA(0): [agp] 12288 kB allocated with handle 0x00000001
(II) MGA(0): [agp] WARP microcode handle = 0xe0000000
(II) MGA(0): [agp] Primary DMA handle = 0xe0008000
(II) MGA(0): [agp] DMA buffers handle = 0xe0108000
(II) MGA(0): [drm] Added 128 65536 byte DMA buffers
(II) MGA(0): [agp] agpTexture handle = 0xe0908000
(II) MGA(0): [agp] agpTexture size: 2816 kb
(II) MGA(0): [drm] Registers handle = 0xe4000000
(II) MGA(0): [drm] Status handle = 0xe0b52000
(II) MGA(0): [dri] visual configs initialized
(II) MGA(0): Memory manager initialized to (0,0) (1280,1227)
(II) MGA(0): Largest offscreen area available: 1280 x 203
(II) MGA(0): Reserved back buffer at offset 0x600000
(II) MGA(0): Reserved depth buffer at offset 0xb00000
(II) MGA(0): Reserved 0 kb for textures at offset 0x1000000
(II) MGA(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        Solid filled trapezoids
        8x8 mono pattern filled rectangles
        8x8 mono pattern filled trapezoids
        Indirect CPU to Screen color expansion
        Screen to Screen color expansion
        Solid Lines
        Dashed Lines
        Scanline Image Writes
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                10 128x128 slots
(==) MGA(0): Backing store disabled
(==) MGA(0): Silken mouse enabled
(**) Option "dpms"
(**) MGA(0): DPMS enabled
(II) MGA(0): Using overlay video
(II) MGA(0): X context handle = 0x1
(II) MGA(0): [drm] installed DRM signal handler
(II) MGA(0): [DRI] installation complete
(II) MGA(0): [drm] Mapped 128 DMA buffers
(II) MGA(0): [drm] dma control initialized, using IRQ 11
(II) MGA(0): Direct rendering enabled
(==) RandR enabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(EE) AIGLX error: dlopen of /usr/lib/dri/mga_dri.so failed (/usr/lib/dri/mga_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0

```

For the record; there is **no** /usr/lib/dri/ here.

Any ideas?

Thanks in advance!
-Mike

---

### Post by mpfleger on 2007-11-06
Oh; I forgot to mention that the default kernel config shows that the appropriate DRI kermel module should have been built as a module, but I couldn't find it. Perhaps the name is something counter-intuitive?

Thanks in advance!
-m

---

### Post by clubsoda on 2007-11-20
> **mpfleger said:**
> ```

(EE) AIGLX error: dlopen of /usr/lib/dri/mga_dri.so failed (/usr/lib/dri/mga_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering

```
Did you solve this already?  I just discovered that my G550 was not enjoying DRI performance either, for the same reason.  Fixed by installing the package **libgl1-mesa-dri**.

Of course, I didn't know that instinctively.  First I used ```
slocate mga_dri.so
``` to see if the file was already installed in some different directory.  No luck, so I went to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and used the second search option, "Search the contents of packages" to find out where I could get that file.  Then I used synaptic to install the package.

My glxgears frame rate jumped from 54 to 308 per second.  Now I can play *Pathogen* properly. :biggrin:

---


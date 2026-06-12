---
title: "Cannot Display This Video Mode"
date: 2011-05-29
forum: Multimedia Software
---

### Post by name_redacted on 2011-05-29
I use natty 64 bit.
I installed a HD 4870
Installed the drivers according to instruction on [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
I ran aticonfig --initial

Still I get "Cannot Display This video Mode" after the grub screen, during boot up.

Monitor preferences applet doesn't seem to work, either - it won't detect the monitor parameters EDID thing.

When I try to open the Catalyst Control Centre I get;  

p, li { white-space: pre-wrap; }  "There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 
 No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."


I've tried sucking my thumb and sighing, but it didn't work.


How do I fix this?


Here are two chunks of xorg log (I cut the non video bits).


 (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[   210.874] (II) LoadModule: "extmod"
[   210.875] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   210.875] (II) Module extmod: vendor="X.Org Foundation"
[   210.875]     compiled for 1.10.1, module version = 1.0.0
[   210.875]     Module class: X.Org Server Extension
[   210.875]     ABI class: X.Org Server Extension, version 5.0
[   210.875] (II) Loading extension MIT-SCREEN-SAVER
[   210.875] (II) Loading extension XFree86-VidModeExtension
[   210.875] (II) Loading extension XFree86-DGA
[   210.875] (II) Loading extension DPMS
[   210.875] (II) Loading extension XVideo
[   210.875] (II) Loading extension XVideo-MotionCompensation
[   210.875] (II) Loading extension X-Resource
[   210.875] (II) LoadModule: "dbe"
[   210.875] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   210.875] (II) Module dbe: vendor="X.Org Foundation"
[   210.875]     compiled for 1.10.1, module version = 1.0.0
[   210.875]     Module class: X.Org Server Extension
[   210.875]     ABI class: X.Org Server Extension, version 5.0
[   210.875] (II) Loading extension DOUBLE-BUFFER
[   210.875] (II) LoadModule: "glx"
[   210.875] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[   210.876] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[   210.876]     compiled for 6.9.0, module version = 1.0.0
[   210.876] (II) Loading extension GLX
[   210.876] (II) LoadModule: "record"
[   210.876] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   210.876] (II) Module record: vendor="X.Org Foundation"
[   210.876]     compiled for 1.10.1, module version = 1.13.0
[   210.876]     Module class: X.Org Server Extension
[   210.876]     ABI class: X.Org Server Extension, version 5.0
[   210.876] (II) Loading extension RECORD
[   210.876] (II) LoadModule: "dri"
[   210.876] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   210.877] (II) Module dri: vendor="X.Org Foundation"
[   210.877]     compiled for 1.10.1, module version = 1.0.0
[   210.877]     ABI class: X.Org Server Extension, version 5.0
[   210.877] (II) Loading extension XFree86-DRI
[   210.877] (II) LoadModule: "dri2"
[   210.877] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   210.877] (II) Module dri2: vendor="X.Org Foundation"
[   210.877]     compiled for 1.10.1, module version = 1.2.0
[   210.877]     ABI class: X.Org Server Extension, version 5.0
[   210.877] (II) Loading extension DRI2
[   210.877] (II) LoadModule: "vesa"
[   210.877] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   210.877] (II) Module vesa: vendor="X.Org Foundation"
[   210.877]     compiled for 1.10.0, module version = 2.3.0
[   210.877]     Module class: X.Org Video Driver
[   210.877]     ABI class: X.Org Video Driver, version 10.0
[   210.877] (II) VESA: driver for VESA chipsets: vesa
[   210.877] (--) using VT number 3

[   211.235] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   211.235] (II) Loading sub module "vbe"
[   211.235] (II) LoadModule: "vbe"
[   211.236] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   211.236] (II) Module vbe: vendor="X.Org Foundation"
[   211.236]     compiled for 1.10.1, module version = 1.1.0
[   211.236]     ABI class: X.Org Video Driver, version 10.0
[   211.236] (II) Loading sub module "int10"
[   211.236] (II) LoadModule: "int10"
[   211.236] (II) Loading /usr/lib/xorg/modules/libint10.so
[   211.236] (II) Module int10: vendor="X.Org Foundation"
[   211.236]     compiled for 1.10.1, module version = 1.0.0
[   211.236]     ABI class: X.Org Video Driver, version 10.0
[   211.236] (II) VESA(0): initializing int10
[   211.236] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   211.236] (II) VESA(0): VESA BIOS detected
[   211.236] (II) VESA(0): VESA VBE Version 3.0
[   211.237] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[   211.237] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[   211.237] (II) VESA(0): VESA VBE OEM Software Rev: 11.3
[   211.237] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   211.237] (II) VESA(0): VESA VBE OEM Product: RV770
[   211.237] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[   211.243] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[   211.243] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[   211.243] (==) VESA(0): RGB weight 888
[   211.243] (==) VESA(0): Default visual is TrueColor
[   211.243] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[   211.243] (II) Loading sub module "ddc"
[   211.243] (II) LoadModule: "ddc"
[   211.243] (II) Module "ddc" already built-in
[   211.243] (II) VESA(0): VESA VBE DDC supported
[   211.243] (II) VESA(0): VESA VBE DDC Level 2
[   211.243] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[   211.259] (II) VESA(0): VESA VBE DDC unkown failure 768
[   211.259] (II) VESA(0): VESA VBE PanelID unknown failure 768
[   211.259] (II) VESA(0): Searching for matching VESA mode(s):
[   211.259] Mode: 100 (640x400)



[   211.274] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[   211.274] (II) VESA(0): Configured Monitor: Using default hsync range of 31.50-48.00 kHz
[   211.274] (II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
[   211.274] (II) VESA(0): Configured Monitor: Using default maximum pixel clock of 65.00 MHz
[   211.274] (WW) VESA(0): Unable to estimate virtual size
[   211.274] (II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "1856x1392" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "1792x1344" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "1400x1050" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "1152x864" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "720x400" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[   211.274] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[   211.275] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[   211.275] (WW) VESA(0): No valid modes left. Trying less strict filter...
[   211.275] (II) VESA(0): Configured Monitor: Using hsync range of 31.50-48.00 kHz
[   211.275] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-70.00 Hz
[   211.275] (II) VESA(0): Configured Monitor: Using maximum pixel clock of 65.00 MHz
[   211.275] (WW) VESA(0): Unable to estimate virtual size
[   211.275] (II) VESA(0): Not using built-in mode "1920x1440" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "1856x1392" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "1792x1344" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "1400x1050" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "1152x864" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "720x400" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
[   211.275] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[   211.275] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[   211.275] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[   211.275] (**) VESA(0): *Built-in mode "1024x768"
[   211.275] (**) VESA(0): *Built-in mode "800x600"
[   211.275] (**) VESA(0): *Built-in mode "640x480"
[   211.275] (==) VESA(0): DPI set to (96, 96)
[   211.275] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (123)
[   211.275] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (122)
[   211.275] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (121)
[   211.275] (**) VESA(0): Using "Shadow Framebuffer"
[   211.275] (II) Loading sub module "shadow"
[   211.275] (II) LoadModule: "shadow"
[   211.275] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   211.275] (II) Module shadow: vendor="X.Org Foundation"
[   211.275]     compiled for 1.10.1, module version = 1.1.0
[   211.275]     ABI class: X.Org ANSI C Emulation, version 0.4
[   211.275] (II) Loading sub module "fb"
[   211.275] (II) LoadModule: "fb"
[   211.276] (II) Loading /usr/lib/xorg/modules/libfb.so
[   211.276] (II) Module fb: vendor="X.Org Foundation"
[   211.276]     compiled for 1.10.1, module version = 1.0.0
[   211.276]     ABI class: X.Org ANSI C Emulation, version 0.4
[   211.276] (==) Depth 24 pixmap format is 32 bpp
[   211.276] (II) Loading sub module "int10"
[   211.276] (II) LoadModule: "int10"
[   211.276] (II) Loading /usr/lib/xorg/modules/libint10.so
[   211.276] (II) Module int10: vendor="X.Org Foundation"
[   211.276]     compiled for 1.10.1, module version = 1.0.0
[   211.276]     ABI class: X.Org Video Driver, version 10.0
[   211.276] (II) VESA(0): initializing int10
[   211.276] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   211.276] (II) VESA(0): VESA BIOS detected
[   211.276] (II) VESA(0): VESA VBE Version 3.0
[   211.276] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[   211.276] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[   211.276] (II) VESA(0): VESA VBE OEM Software Rev: 11.3
[   211.276] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   211.276] (II) VESA(0): VESA VBE OEM Product: RV770
[   211.276] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[   211.278] (II) VESA(0): virtual address = 0x7fe85a578000,
    physical address = 0xd0000000, size = 16777216
[   211.286] (II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
[   211.286] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[   211.356] (==) VESA(0): Default visual is TrueColor
[   211.356] (==) VESA(0): Backing store disabled
[   211.356] (==) VESA(0): DPMS enabled
[   211.356] (==) RandR enabled
[   211.356] (II) Initializing built-in extension Generic Event Extension
[   211.356] (II) Initializing built-in extension SHAPE
[   211.356] (II) Initializing built-in extension MIT-SHM
[   211.356] (II) Initializing built-in extension XInputExtension
[   211.356] (II) Initializing built-in extension XTEST
[   211.356] (II) Initializing built-in extension BIG-REQUESTS
[   211.356] (II) Initializing built-in extension SYNC
[   211.356] (II) Initializing built-in extension XKEYBOARD
[   211.356] (II) Initializing built-in extension XC-MISC
[   211.356] (II) Initializing built-in extension SECURITY
[   211.356] (II) Initializing built-in extension XINERAMA
[   211.356] (II) Initializing built-in extension XFIXES
[   211.356] (II) Initializing built-in extension RENDER
[   211.356] (II) Initializing built-in extension RANDR
[   211.356] (II) Initializing built-in extension COMPOSITE
[   211.356] (II) Initializing built-in extension DAMAGE
[   211.356] (II) Initializing built-in extension GESTURE
[   211.358] (EE) GLX error: Can not get required symbols.
[   211.368] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm

Wassa wrongs wiv it?

Help appreciated!

---

### Post by name_redacted on 2011-06-02
Fixed!

Simply needed to delete the old xorg.conf files and make a new one with aticonfig --initial, then set the resolution and refresh rate I wanted with aticofig also.

---


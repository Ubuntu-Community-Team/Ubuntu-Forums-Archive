---
title: "rebooting gives me only black screen"
date: 2009-02-05
forum: Multimedia Software
---

### Post by forestwalkerjoe on 2009-02-05
I have several issues.. and i have posted to various places in here.. if some one could help me with these.. i will feel better about Ubuntu support.. but for now..  
I  have this intermittent problem. 
some one was trying to work it out for me.. but it comes and goes. 

I keep having issues with failure to "something" at boot up. It seems like the code that the computer reads.. to start functions.. is failing to read the part about refresh rate or loading the driver that runs the Graphics card. 
When i log into the Win side of my duel os.. there isn't a problem.. so i can safely say.. its not the hardware. 
it was EVERY TIME.. each and every time i would shut down.. and then later restart.. i would have to fight to get it to load the screen.. JUST a black screen.. no sounds nothing. 
the guy who helped me had me request some sort of update. to some config file.. and it went away for a few days. sudo dpkg-reconfigure -phigh xserver-xorg
My thoughts are.. 
Is it possible to load the code into the kernal or some thing? so that it will find and load the right stuff each time.. with no possible failure? 
Screen failure is very frustrating. 
When it fails.. there is just a black screen.. no sounds.. no way for me to solve the issue other than hold the button down till the system turns off. NOT great on the system. 
I am sure there is a solve. I am just not great enough with HOW this stuff works or what code to write.

---

### Post by forestwalkerjoe on 2009-02-09
Sony / Viao older lapptop. Savage X video card.
Driver installed..
boot up is : makes to Ubuntu orange timer screen.. X never shows up.. can hear boot up but can not see.. can not see mouse and keyboard is not responding. Some times i can move mouse with out seeing it to hit restart. REISUB doesnt work on this config.
here is the out put from the sudo gedit rj@rj-laptop:~$ sudo gedit /var/log/Xorg.*.log
I know this is terribly long.. i am not trying to FLOOD or any thing.. if some one would help by answering my own thread.. please? i am getting desperate.


 > X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux rj-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 9 08:50:01 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section. Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) | |-->Monitor "Configured Monitor"
(**) | |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified. Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Entry deleted from font path.
(==) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/Type1,
/usr/share/fonts/X11/100dpi,
/usr/share/fonts/X11/75dpi,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
X.Org ANSI C Emulation: 0.4
X.Org Video Driver: 4.1
X.Org XInput driver : 2.1
X.Org Server Extension : 1.1
X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) S3 Inc. 86C270-294 Savage/IX-MV rev 17, Mem @ 0xf0000000/0, BIOS @ 0x????????/65536
(II) System resource ranges:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
compiled for 1.5.2, module version = 2.1.0
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.13.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched savage from file name savage.ids
(==) Matched savage for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "savage"

(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
compiled for 1.5.0, module version = 2.2.1
Module class: X.Org Video Driver
ABI class: X.Org Video Driver, version 4.1
(II) SAVAGE: driver (version 2.2.1) for S3 Savage chipsets: Savage4,
Savage3D, Savage3D-MV, Savage2000, Savage/MX-MV, Savage/MX,
Savage/IX-MV, Savage/IX, ProSavage PM133, ProSavage KM133,
Twister PN133, Twister KN133, SuperSavage/MX 128, SuperSavage/MX 64,
SuperSavage/MX 64C, SuperSavage/IX 128, SuperSavage/IX 128,
SuperSavage/IX 64, SuperSavage/IX 64, SuperSavage/IXC 64,
SuperSavage/IXC 64, ProSavage DDR, ProSavage DDR-K
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
(II) resource ranges after probing:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] 0 0 0x000a0000 - 0x000affff (0x10000) MS[b]
[5] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS[b]
[6] 0 0 0x000b8000 - 0x000bffff (0x8000) MS[b]
[7] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[8] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[9] 0 0 0x000003b0 - 0x000003bb (0xc) IS[b]
[10] 0 0 0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 0.1.0
ABI class: X.Org Video Driver, version 4.1
(II) SAVAGE(0): Creating default Display subsection in Screen section
"Default Screen" for depth/fbbpp 16/16
(==) SAVAGE(0): Depth 16, (--) framebuffer bpp 16
(==) SAVAGE(0): RGB weight 565
(==) SAVAGE(0): Default visual is TrueColor
(II) SAVAGE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) SAVAGE(0): Using XAA acceleration architecture
(==) SAVAGE(0): Using HW cursor
(==) SAVAGE(0): Using video BIOS to set modes
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.1.0
ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org Video Driver, version 4.1
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 2.0
(II) SAVAGE(0): VESA VBE Total Mem: 8192 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Incorporated. M7 BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 1.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 2.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 1.1
(--) SAVAGE(0): Chip: id 8c12, "Savage/IX-MV"
(--) SAVAGE(0): Engine: "MobileSavage"
(--) SAVAGE(0): AGP card detected
(==) SAVAGE(0): Using AGP DMA
(II) SAVAGE(0): Savage3D/MX/IX does not support command DMA.
(==) SAVAGE(0): Will try only vertex DMA mode
(==) SAVAGE(0): Using AGP 1x mode
(==) SAVAGE(0): Using 16 MB AGP aperture
(==) SAVAGE(0): Using gamma correction (1.0, 1.0, 1.0)
(--) SAVAGE(0): probed videoram: 8192k
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SAVAGE(0): No DDC signal
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) SAVAGE(0): I2C bus "I2C bus" initialized.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" registered at address 0xA0.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" removed.
(--) SAVAGE(0): Detected current MCLK value of 83.045 MHz
(--) SAVAGE(0): 1024x768 TFT LCD panel detected and active
(--) SAVAGE(0): - Limiting video mode to 1024x768
(--) SAVAGE(0): Found 13 modes at this depth:
[10e] 320 x 200, 70Hz
[111] 640 x 480, 60Hz, 72Hz, 75Hz, 85Hz, 100Hz
[114] 800 x 600, 60Hz, 72Hz, 75Hz, 85Hz, 100Hz
[117] 1024 x 768, 60Hz, 70Hz, 75Hz, 85Hz, 43Hz, 100Hz
[11a] 1280 x 1024, 60Hz, 75Hz, 85Hz, 43Hz
[11d] 640 x 400, 70Hz
[122] 1600 x 1200, 48Hz, 60Hz, 75Hz, 85Hz
[133] 320 x 240, 72Hz
[13c] 1400 x 1050, 60Hz, 75Hz
[143] 400 x 300, 72Hz
[153] 512 x 384, 70Hz
[173] 720 x 480, 75Hz
[178] 720 x 576, 75Hz
(II) SAVAGE(0): Configured Monitor: Using hsync range of 31.50-47.82 kHz
(II) SAVAGE(0): Configured Monitor: Using vrefresh range of 56.00-59.92 Hz
(II) SAVAGE(0): Configured Monitor: Using maximum pixel clock of 63.50 MHz
(II) SAVAGE(0): Estimated virtual size for aspect ratio 1.3333 is 1024x768
(II) SAVAGE(0): Clock range: 10.00 to 250.00 MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x350 85Hz.
(II) SAVAGE(0): Not using default mode "640x350" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 320x175 85Hz.
(II) SAVAGE(0): Not using default mode "320x175" (no mode of this name)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(II) SAVAGE(0): Not using default mode "640x400" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 10e at 70Hz.
(II) SAVAGE(0): Not using default mode "320x200" (vrefresh out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 720x400 85Hz.
(II) SAVAGE(0): Not using default mode "720x400" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 360x200 85Hz.
(II) SAVAGE(0): Not using default mode "360x200" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 72Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 72Hz.
(II) SAVAGE(0): Not using default mode "800x600" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 75Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x960" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1280x960" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 60Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 75Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 85Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 72Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1792x1344" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 60Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1792x1344" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 75Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 60Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 75Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 60Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 75Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using default mode "832x624" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 416x312 74Hz.
(II) SAVAGE(0): Not using default mode "416x312" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 60Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 70Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 74Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 100Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1360x768" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 680x384 59Hz.
(II) SAVAGE(0): Not using default mode "680x384" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1360x768" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 680x384 59Hz.
(II) SAVAGE(0): Not using default mode "680x384" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 59Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 70Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 74Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 85Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1440x900" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 720x450 59Hz.
(II) SAVAGE(0): Not using default mode "720x450" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1600x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 800x512 60Hz.
(II) SAVAGE(0): Not using default mode "800x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 59Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 69Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 74Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 85Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1080" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x540 59Hz.
(II) SAVAGE(0): Not using default mode "960x540" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1200" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 59Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 85Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Virtual size is 1024x768 (pitch 1024)
(**) SAVAGE(0): *Driver mode "1024x768": 56.0 MHz, 47.3 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "1024x768"x59.9 56.00 1024 1072 1104 1184 768 771 775 790 +hsync -vsync (47.3 kHz)
(**) SAVAGE(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"x60.3 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"x56.2 36.00 800 824 896 1024 600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "640x480"x59.9 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)
(**) SAVAGE(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"x60.3 20.00 400 420 484 528 300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"x56.3 18.00 400 412 448 512 300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) SAVAGE(0): Modeline "320x240"x60.1 12.59 320 328 376 400 240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) SAVAGE(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.2.0
ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) do I need RAC? No, I don't.
(II) resource ranges after preInit:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] 0 0 0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
[5] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
[6] 0 0 0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
[7] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[8] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[9] 0 0 0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
[10] 0 0 0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 2.0
(II) SAVAGE(0): VESA VBE Total Mem: 8192 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Incorporated. M7 BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 1.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 2.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 1.1
(II) SAVAGE(0): 4740 kB of Videoram needed for 3D; 8192 kB of Videoram available
(II) SAVAGE(0): Sufficient Videoram available for 3D
(II) SAVAGE(0): [drm] bpp: 16 depth: 16
(II) SAVAGE(0): [drm] Sarea 2200+284: 2484
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
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "savage" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) SAVAGE(0): [drm] Using the DRM lock SAREA also for drawables.
(II) SAVAGE(0): [drm] framebuffer handle = 0xf0000000
(II) SAVAGE(0): [drm] added 1 reserved context for kernel
(II) SAVAGE(0): X context handle = 0x1
(II) SAVAGE(0): [drm] installed DRM signal handler
(II) SAVAGE(0): [agp] Mode 0x1f000201 [AGP 0x8086/0x7190; Card 0x5333/0x8c12]
(II) SAVAGE(0): [agp] 16384 kB allocated with handle 0x00000001
(II) SAVAGE(0): [agp] DMA buffers handle = 0x40000000
(II) SAVAGE(0): [agp] agpTextures handle = 0x40200000
(II) SAVAGE(0): [drm] aperture handle = 0xf2000000
(II) SAVAGE(0): [drm] Enabling ShadowStatus for DRI.
(II) SAVAGE(0): [drm] Status handle = 0x0faea000
(II) SAVAGE(0): [drm] Status page mapped at 0xb200b000
(II) SAVAGE(0): [drm] Added 32 65536 byte DMA buffers
(II) SAVAGE(0): [dri] visual configs initialized
(**) SAVAGE(0): DRI is enabled
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): virtualX:1024,virtualY:768
(II) SAVAGE(0): bpp:16,tiledwidthBytes:2048,tiledBufferSize:157286 4
(II) SAVAGE(0): bpp:16,widthBytes:2048,BufferSize:1572864
(II) SAVAGE(0): videoRambytes:0x00800000
(II) SAVAGE(0): textureSize:0x0015f000
(II) SAVAGE(0): textureSize:0x0015f000
(II) SAVAGE(0): textureOffset:0x00680000
(II) SAVAGE(0): depthOffset:0x00500000,depthPitch:2048
(II) SAVAGE(0): backOffset:0x00380000,backPitch:2048
(II) SAVAGE(0): Reserved back buffer at offset 0x380000
(II) SAVAGE(0): Reserved depth buffer at offset 0x500000
(II) SAVAGE(0): Reserved 1404 kb for textures at offset 0x680000
(II) SAVAGE(0): Using 1023 lines for offscreen memory.
(II) SAVAGE(0): Using XFree86 Acceleration Architecture (XAA)
Screen to screen bit blits
Solid filled rectangles
8x8 mono pattern filled rectangles
Indirect CPU to Screen color expansion
Solid Lines
Image Writes
Setting up tile and stipple cache:
28 128x128 slots
7 256x256 slots
(==) SAVAGE(0): Backing store disabled
(II) SAVAGE(0): DPMS enabled
(II) SAVAGE(0): [DRI] installation complete
(II) SAVAGE(0): [junkers]pSAVAGEDRIServer:
(II) SAVAGE(0): [junkers] reserved_map_agpstart:0x00000000
(II) SAVAGE(0): [junkers] reserved_map_idx:0x00000000
(II) SAVAGE(0): [junkers] sarea_priv_offset:0x00000000
(II) SAVAGE(0): [junkers] chipset:0x00000000
(II) SAVAGE(0): [junkers] sgram:0x00000000
(II) SAVAGE(0): [junkers] frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers] frontOffset:0x00000000
(II) SAVAGE(0): [junkers] frontPitch:0x00000800
(II) SAVAGE(0): [junkers] backbufferSize:0x00180000
(II) SAVAGE(0): [junkers] backOffset:0x00380000
(II) SAVAGE(0): [junkers] backPitch:0x00000800
(II) SAVAGE(0): [junkers] depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers] depthOffset:0x00500000
(II) SAVAGE(0): [junkers] depthPitch:0x00000800
(II) SAVAGE(0): [junkers] textureOffset:0x00680000
(II) SAVAGE(0): [junkers] textureSize:0x0015f000
(II) SAVAGE(0): [junkers] textureSize:0x0015f000
(II) SAVAGE(0): [junkers] logTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers] agp:handle:0x00000001
(II) SAVAGE(0): [junkers] agpffset:0x01000000
(II) SAVAGE(0): [junkers] agp:size:0x01000000
(II) SAVAGE(0): [junkers] agp:map:0x00000000
(II) SAVAGE(0): [junkers] registers:handle:0xf1000000
(II) SAVAGE(0): [junkers] registersffset:0x00000000
(II) SAVAGE(0): [junkers] registers:size:0x00080000
(II) SAVAGE(0): [junkers] registers:map:0x00000000
(II) SAVAGE(0): [junkers] status:handle:0x0faea000
(II) SAVAGE(0): [junkers] statusffset:0x00000000
(II) SAVAGE(0): [junkers] status:size:0x00001000
(II) SAVAGE(0): [junkers] status:map:0xb200b000
(II) SAVAGE(0): [junkers] agpTextures:handle:0x40200000
(II) SAVAGE(0): [junkers] agpTexturesffset:0x00200000
(II) SAVAGE(0): [junkers] agpTextures:size:0x00e00000
(II) SAVAGE(0): [junkers] apgTextures:map:0x00000000
(II) SAVAGE(0): [junkers] logAgpTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers] cmdDma:handle:0x00000000
(II) SAVAGE(0): [junkers] cmdDmaffset:0x00000000
(II) SAVAGE(0): [junkers] cmdDma:size:0x00000000
(II) SAVAGE(0): [junkers] cmdDma:map:0x00000000
(II) SAVAGE(0): [junkers]pSAVAGEDRI:
(II) SAVAGE(0): [junkers] chipset:0x00000002
(II) SAVAGE(0): [junkers] width:0x00000400
(II) SAVAGE(0): [junkers] height:0x00000300
(II) SAVAGE(0): [junkers] mem:0x00800000
(II) SAVAGE(0): [junkers] cpp:2
(II) SAVAGE(0): [junkers] zpp:2
(II) SAVAGE(0): [junkers] agpMode:1
(II) SAVAGE(0): [junkers] bufferSize:65536
(II) SAVAGE(0): [junkers] frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers] frontOffset:0x00000000
(II) SAVAGE(0): [junkers] backbufferSize:0x00180000
(II) SAVAGE(0): [junkers] backOffset:0x00380000
(II) SAVAGE(0): [junkers] depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers] depthOffset:0x00500000
(II) SAVAGE(0): [junkers] textureOffset:0x00680000
(II) SAVAGE(0): [junkers] textureSize:0x00140000
(II) SAVAGE(0): [junkers] logTextureGranularity:0x00000011
(II) SAVAGE(0): [junkers] agpTextureHandle:0x40200000
(II) SAVAGE(0): [junkers] agpTextureSize:0x00e00000
(II) SAVAGE(0): [junkers] logAgpTextureGranularity:0x00000014
(II) SAVAGE(0): [junkers] apertureHandle:0xf2000000
(II) SAVAGE(0): [junkers] apertureSize:0x05000000
(II) SAVAGE(0): [junkers] aperturePitch:0x00002000
(II) SAVAGE(0): [junkers] statusHandle:0x0faea000
(II) SAVAGE(0): [junkers] statusSize:0x00001000
(II) SAVAGE(0): [junkers] sarea_priv_offset:0x00000898
(II) SAVAGE(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: Loaded and initialized /usr/lib/dri/savage_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 2.0.99
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 0.15.2
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(**) Option "Device" "/dev/input/event6"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event5"
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device HID 1241:1111
(**) HID 1241:1111: always reports core events
(**) HID 1241:1111: Device: "/dev/input/event2"
(II) HID 1241:1111: Found x and y relative axes
(II) HID 1241:1111: Found 3 mouse buttons
(II) HID 1241:1111: Configuring as mouse
(II) XINPUT: Adding extended input device "HID 1241:1111" (type: MOUSE)
(**) HID 1241:1111: YAxisMapping: buttons 4 and 5
(**) HID 1241:1111: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Sony Vaio Keys
(**) Sony Vaio Keys: always reports core events
(**) Sony Vaio Keys: Device: "/dev/input/event7"
(II) Sony Vaio Keys: Found keys
(II) Sony Vaio Keys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Sony Vaio Keys: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Sony Vaio Keys: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Sony Vaio Keys: xkb_layout: "us"


AGAIN.. i am very sorry i had to put the whole LOG up here.. but i have no idea what parts are related to my issues.. and wanted to make sure that "IF" some one did choose to help me that they had all the info.. which i can not decipher.
My Keyboard config is differnt than most as well and the special HOT keys that are related to this lappys build dont work.. IF i do some times get into the ubuntu install.. which once in a long while Does happen.. all the worty keys work.. but the Blue hot keys using FN to activate dont. As well as the fact that the above log shows an issue with REFRESH rates and finding the right way to load what i think is XORG stuff.
So.. some times NO keybard , mouse or screen. Can some one help me edit some thing to tell the system how to boot up right?
thanks
FWJ

---

### Post by redroad55 on 2009-02-09
when posting a log like you have use "#" that will make it easier to get thru .. So for example to fix your post at the bottom select edit and then sweep the field of your log then right click and select copy .. hit the space bar .. the field you selected will disappear .. then hit the "#" mark at the top of the page then right click between the 2 brackets and paste .. then hit save..this will make it easier to get thru..```
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux rj-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
Before reporting problems, check http://wiki.x.org
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 9 08:50:01 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section. Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) | |-->Monitor "Configured Monitor"
(**) | |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified. Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Entry deleted from font path.
(==) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/Type1,
/usr/share/fonts/X11/100dpi,
/usr/share/fonts/X11/75dpi,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
X.Org ANSI C Emulation: 0.4
X.Org Video Driver: 4.1
X.Org XInput driver : 2.1
X.Org Server Extension : 1.1
X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) S3 Inc. 86C270-294 Savage/IX-MV rev 17, Mem @ 0xf0000000/0, BIOS @ 0x????????/65536
(II) System resource ranges:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
compiled for 1.5.2, module version = 2.1.0
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.13.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched savage from file name savage.ids
(==) Matched savage for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "savage"

(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
compiled for 1.5.0, module version = 2.2.1
Module class: X.Org Video Driver
ABI class: X.Org Video Driver, version 4.1
(II) SAVAGE: driver (version 2.2.1) for S3 Savage chipsets: Savage4,
Savage3D, Savage3D-MV, Savage2000, Savage/MX-MV, Savage/MX,
Savage/IX-MV, Savage/IX, ProSavage PM133, ProSavage KM133,
Twister PN133, Twister KN133, SuperSavage/MX 128, SuperSavage/MX 64,
SuperSavage/MX 64C, SuperSavage/IX 128, SuperSavage/IX 128,
SuperSavage/IX 64, SuperSavage/IX 64, SuperSavage/IXC 64,
SuperSavage/IXC 64, ProSavage DDR, ProSavage DDR-K
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
(II) resource ranges after probing:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] 0 0 0x000a0000 - 0x000affff (0x10000) MS[b]
[5] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS[b]
[6] 0 0 0x000b8000 - 0x000bffff (0x8000) MS[b]
[7] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[8] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[9] 0 0 0x000003b0 - 0x000003bb (0xc) IS[b]
[10] 0 0 0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 0.1.0
ABI class: X.Org Video Driver, version 4.1
(II) SAVAGE(0): Creating default Display subsection in Screen section
"Default Screen" for depth/fbbpp 16/16
(==) SAVAGE(0): Depth 16, (--) framebuffer bpp 16
(==) SAVAGE(0): RGB weight 565
(==) SAVAGE(0): Default visual is TrueColor
(II) SAVAGE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) SAVAGE(0): Using XAA acceleration architecture
(==) SAVAGE(0): Using HW cursor
(==) SAVAGE(0): Using video BIOS to set modes
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.1.0
ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org Video Driver, version 4.1
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 2.0
(II) SAVAGE(0): VESA VBE Total Mem: 8192 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Incorporated. M7 BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 1.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 2.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 1.1
(--) SAVAGE(0): Chip: id 8c12, "Savage/IX-MV"
(--) SAVAGE(0): Engine: "MobileSavage"
(--) SAVAGE(0): AGP card detected
(==) SAVAGE(0): Using AGP DMA
(II) SAVAGE(0): Savage3D/MX/IX does not support command DMA.
(==) SAVAGE(0): Will try only vertex DMA mode
(==) SAVAGE(0): Using AGP 1x mode
(==) SAVAGE(0): Using 16 MB AGP aperture
(==) SAVAGE(0): Using gamma correction (1.0, 1.0, 1.0)
(--) SAVAGE(0): probed videoram: 8192k
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SAVAGE(0): No DDC signal
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) SAVAGE(0): I2C bus "I2C bus" initialized.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" registered at address 0xA0.
(II) SAVAGE(0): I2C device "I2C bus:ddc2" removed.
(--) SAVAGE(0): Detected current MCLK value of 83.045 MHz
(--) SAVAGE(0): 1024x768 TFT LCD panel detected and active
(--) SAVAGE(0): - Limiting video mode to 1024x768
(--) SAVAGE(0): Found 13 modes at this depth:
[10e] 320 x 200, 70Hz
[111] 640 x 480, 60Hz, 72Hz, 75Hz, 85Hz, 100Hz
[114] 800 x 600, 60Hz, 72Hz, 75Hz, 85Hz, 100Hz
[117] 1024 x 768, 60Hz, 70Hz, 75Hz, 85Hz, 43Hz, 100Hz
[11a] 1280 x 1024, 60Hz, 75Hz, 85Hz, 43Hz
[11d] 640 x 400, 70Hz
[122] 1600 x 1200, 48Hz, 60Hz, 75Hz, 85Hz
[133] 320 x 240, 72Hz
[13c] 1400 x 1050, 60Hz, 75Hz
[143] 400 x 300, 72Hz
[153] 512 x 384, 70Hz
[173] 720 x 480, 75Hz
[178] 720 x 576, 75Hz
(II) SAVAGE(0): Configured Monitor: Using hsync range of 31.50-47.82 kHz
(II) SAVAGE(0): Configured Monitor: Using vrefresh range of 56.00-59.92 Hz
(II) SAVAGE(0): Configured Monitor: Using maximum pixel clock of 63.50 MHz
(II) SAVAGE(0): Estimated virtual size for aspect ratio 1.3333 is 1024x768
(II) SAVAGE(0): Clock range: 10.00 to 250.00 MHz
(--) SAVAGE(0): No suitable BIOS mode found for 640x350 85Hz.
(II) SAVAGE(0): Not using default mode "640x350" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 320x175 85Hz.
(II) SAVAGE(0): Not using default mode "320x175" (no mode of this name)
(--) SAVAGE(0): Chose mode 11d at 70Hz.
(II) SAVAGE(0): Not using default mode "640x400" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 10e at 70Hz.
(II) SAVAGE(0): Not using default mode "320x200" (vrefresh out of range)
(--) SAVAGE(0): No suitable BIOS mode found for 720x400 85Hz.
(II) SAVAGE(0): Not using default mode "720x400" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 360x200 85Hz.
(II) SAVAGE(0): Not using default mode "360x200" (no mode of this name)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Chose mode 111 at 72Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 111 at 75Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(II) SAVAGE(0): Not using default mode "320x240" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 114 at 72Hz.
(II) SAVAGE(0): Not using default mode "800x600" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(II) SAVAGE(0): Not using default mode "400x300" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (vrefresh out of range)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 70Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 153 at 70Hz.
(II) SAVAGE(0): Not using default mode "512x384" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 75Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x960" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1280x960" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 111 at 85Hz.
(II) SAVAGE(0): Not using default mode "640x480" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 60Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 75Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1280x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 640x512 85Hz.
(II) SAVAGE(0): Not using default mode "640x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 72Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 75Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1600x1200" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 114 at 85Hz.
(II) SAVAGE(0): Not using default mode "800x600" (hsync out of range)
(II) SAVAGE(0): Not using default mode "1792x1344" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 60Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1792x1344" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 896x672 75Hz.
(II) SAVAGE(0): Not using default mode "896x672" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 60Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1856x1392" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 928x696 75Hz.
(II) SAVAGE(0): Not using default mode "928x696" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 60Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 75Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 832x624 74Hz.
(II) SAVAGE(0): Not using default mode "832x624" (no mode of this name)
(--) SAVAGE(0): No suitable BIOS mode found for 416x312 74Hz.
(II) SAVAGE(0): Not using default mode "416x312" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 60Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 70Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 74Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 85Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1152x864" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 576x432 100Hz.
(II) SAVAGE(0): Not using default mode "576x432" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1360x768" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 680x384 59Hz.
(II) SAVAGE(0): Not using default mode "680x384" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1360x768" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 680x384 59Hz.
(II) SAVAGE(0): Not using default mode "680x384" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 59Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 70Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 74Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1400x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 700x525 85Hz.
(II) SAVAGE(0): Not using default mode "700x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1440x900" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 720x450 59Hz.
(II) SAVAGE(0): Not using default mode "720x450" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1600x1024" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 800x512 60Hz.
(II) SAVAGE(0): Not using default mode "800x512" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 59Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 60Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 69Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 74Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1680x1050" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 840x525 85Hz.
(II) SAVAGE(0): Not using default mode "840x525" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1080" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x540 59Hz.
(II) SAVAGE(0): Not using default mode "960x540" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1200" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x600 59Hz.
(II) SAVAGE(0): Not using default mode "960x600" (no mode of this name)
(II) SAVAGE(0): Not using default mode "1920x1440" (width too large for virtual size)
(--) SAVAGE(0): No suitable BIOS mode found for 960x720 85Hz.
(II) SAVAGE(0): Not using default mode "960x720" (no mode of this name)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 117 at 75Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(II) SAVAGE(0): Not using default mode "2048x1536" (width too large for virtual size)
(--) SAVAGE(0): Chose mode 117 at 85Hz.
(II) SAVAGE(0): Not using default mode "1024x768" (hsync out of range)
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 114 at 60Hz.
(--) SAVAGE(0): Chose mode 111 at 60Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 143 at 72Hz.
(--) SAVAGE(0): Chose mode 133 at 72Hz.
(--) SAVAGE(0): Virtual size is 1024x768 (pitch 1024)
(**) SAVAGE(0): *Driver mode "1024x768": 56.0 MHz, 47.3 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "1024x768"x59.9 56.00 1024 1072 1104 1184 768 771 775 790 +hsync -vsync (47.3 kHz)
(**) SAVAGE(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SAVAGE(0): Modeline "800x600"x60.3 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SAVAGE(0): Modeline "800x600"x56.2 36.00 800 824 896 1024 600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SAVAGE(0): Modeline "640x480"x59.9 25.18 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)
(**) SAVAGE(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"x60.3 20.00 400 420 484 528 300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SAVAGE(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) SAVAGE(0): Modeline "400x300"x56.3 18.00 400 412 448 512 300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) SAVAGE(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) SAVAGE(0): Modeline "320x240"x60.1 12.59 320 328 376 400 240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) SAVAGE(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.2.0
ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) do I need RAC? No, I don't.
(II) resource ranges after preInit:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] 0 0 0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
[5] 0 0 0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
[6] 0 0 0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
[7] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[8] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[9] 0 0 0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
[10] 0 0 0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SAVAGE(0): initializing int10
(II) SAVAGE(0): Primary V_BIOS segment is: 0xc000
(II) SAVAGE(0): VESA BIOS detected
(II) SAVAGE(0): VESA VBE Version 2.0
(II) SAVAGE(0): VESA VBE Total Mem: 8192 kB
(II) SAVAGE(0): VESA VBE OEM: S3 Incorporated. M7 BIOS
(II) SAVAGE(0): VESA VBE OEM Software Rev: 1.0
(II) SAVAGE(0): VESA VBE OEM Vendor: S3 Incorporated.
(II) SAVAGE(0): VESA VBE OEM Product: VBE 2.0
(II) SAVAGE(0): VESA VBE OEM Product Rev: Rev 1.1
(II) SAVAGE(0): 4740 kB of Videoram needed for 3D; 8192 kB of Videoram available
(II) SAVAGE(0): Sufficient Videoram available for 3D
(II) SAVAGE(0): [drm] bpp: 16 depth: 16
(II) SAVAGE(0): [drm] Sarea 2200+284: 2484
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
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "savage" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) SAVAGE(0): [drm] Using the DRM lock SAREA also for drawables.
(II) SAVAGE(0): [drm] framebuffer handle = 0xf0000000
(II) SAVAGE(0): [drm] added 1 reserved context for kernel
(II) SAVAGE(0): X context handle = 0x1
(II) SAVAGE(0): [drm] installed DRM signal handler
(II) SAVAGE(0): [agp] Mode 0x1f000201 [AGP 0x8086/0x7190; Card 0x5333/0x8c12]
(II) SAVAGE(0): [agp] 16384 kB allocated with handle 0x00000001
(II) SAVAGE(0): [agp] DMA buffers handle = 0x40000000
(II) SAVAGE(0): [agp] agpTextures handle = 0x40200000
(II) SAVAGE(0): [drm] aperture handle = 0xf2000000
(II) SAVAGE(0): [drm] Enabling ShadowStatus for DRI.
(II) SAVAGE(0): [drm] Status handle = 0x0faea000
(II) SAVAGE(0): [drm] Status page mapped at 0xb200b000
(II) SAVAGE(0): [drm] Added 32 65536 byte DMA buffers
(II) SAVAGE(0): [dri] visual configs initialized
(**) SAVAGE(0): DRI is enabled
(--) SAVAGE(0): Chose mode 117 at 60Hz.
(II) SAVAGE(0): virtualX:1024,virtualY:768
(II) SAVAGE(0): bpp:16,tiledwidthBytes:2048,tiledBufferSize:157286 4
(II) SAVAGE(0): bpp:16,widthBytes:2048,BufferSize:1572864
(II) SAVAGE(0): videoRambytes:0x00800000
(II) SAVAGE(0): textureSize:0x0015f000
(II) SAVAGE(0): textureSize:0x0015f000
(II) SAVAGE(0): textureOffset:0x00680000
(II) SAVAGE(0): depthOffset:0x00500000,depthPitch:2048
(II) SAVAGE(0): backOffset:0x00380000,backPitch:2048
(II) SAVAGE(0): Reserved back buffer at offset 0x380000
(II) SAVAGE(0): Reserved depth buffer at offset 0x500000
(II) SAVAGE(0): Reserved 1404 kb for textures at offset 0x680000
(II) SAVAGE(0): Using 1023 lines for offscreen memory.
(II) SAVAGE(0): Using XFree86 Acceleration Architecture (XAA)
Screen to screen bit blits
Solid filled rectangles
8x8 mono pattern filled rectangles
Indirect CPU to Screen color expansion
Solid Lines
Image Writes
Setting up tile and stipple cache:
28 128x128 slots
7 256x256 slots
(==) SAVAGE(0): Backing store disabled
(II) SAVAGE(0): DPMS enabled
(II) SAVAGE(0): [DRI] installation complete
(II) SAVAGE(0): [junkers]pSAVAGEDRIServer:
(II) SAVAGE(0): [junkers] reserved_map_agpstart:0x00000000
(II) SAVAGE(0): [junkers] reserved_map_idx:0x00000000
(II) SAVAGE(0): [junkers] sarea_priv_offset:0x00000000
(II) SAVAGE(0): [junkers] chipset:0x00000000
(II) SAVAGE(0): [junkers] sgram:0x00000000
(II) SAVAGE(0): [junkers] frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers] frontOffset:0x00000000
(II) SAVAGE(0): [junkers] frontPitch:0x00000800
(II) SAVAGE(0): [junkers] backbufferSize:0x00180000
(II) SAVAGE(0): [junkers] backOffset:0x00380000
(II) SAVAGE(0): [junkers] backPitch:0x00000800
(II) SAVAGE(0): [junkers] depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers] depthOffset:0x00500000
(II) SAVAGE(0): [junkers] depthPitch:0x00000800
(II) SAVAGE(0): [junkers] textureOffset:0x00680000
(II) SAVAGE(0): [junkers] textureSize:0x0015f000
(II) SAVAGE(0): [junkers] textureSize:0x0015f000
(II) SAVAGE(0): [junkers] logTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers] agp:handle:0x00000001
(II) SAVAGE(0): [junkers] agpffset:0x01000000
(II) SAVAGE(0): [junkers] agp:size:0x01000000
(II) SAVAGE(0): [junkers] agp:map:0x00000000
(II) SAVAGE(0): [junkers] registers:handle:0xf1000000
(II) SAVAGE(0): [junkers] registersffset:0x00000000
(II) SAVAGE(0): [junkers] registers:size:0x00080000
(II) SAVAGE(0): [junkers] registers:map:0x00000000
(II) SAVAGE(0): [junkers] status:handle:0x0faea000
(II) SAVAGE(0): [junkers] statusffset:0x00000000
(II) SAVAGE(0): [junkers] status:size:0x00001000
(II) SAVAGE(0): [junkers] status:map:0xb200b000
(II) SAVAGE(0): [junkers] agpTextures:handle:0x40200000
(II) SAVAGE(0): [junkers] agpTexturesffset:0x00200000
(II) SAVAGE(0): [junkers] agpTextures:size:0x00e00000
(II) SAVAGE(0): [junkers] apgTextures:map:0x00000000
(II) SAVAGE(0): [junkers] logAgpTextureGranularity:0x00000000
(II) SAVAGE(0): [junkers] cmdDma:handle:0x00000000
(II) SAVAGE(0): [junkers] cmdDmaffset:0x00000000
(II) SAVAGE(0): [junkers] cmdDma:size:0x00000000
(II) SAVAGE(0): [junkers] cmdDma:map:0x00000000
(II) SAVAGE(0): [junkers]pSAVAGEDRI:
(II) SAVAGE(0): [junkers] chipset:0x00000002
(II) SAVAGE(0): [junkers] width:0x00000400
(II) SAVAGE(0): [junkers] height:0x00000300
(II) SAVAGE(0): [junkers] mem:0x00800000
(II) SAVAGE(0): [junkers] cpp:2
(II) SAVAGE(0): [junkers] zpp:2
(II) SAVAGE(0): [junkers] agpMode:1
(II) SAVAGE(0): [junkers] bufferSize:65536
(II) SAVAGE(0): [junkers] frontbufferSize:0x00180000
(II) SAVAGE(0): [junkers] frontOffset:0x00000000
(II) SAVAGE(0): [junkers] backbufferSize:0x00180000
(II) SAVAGE(0): [junkers] backOffset:0x00380000
(II) SAVAGE(0): [junkers] depthbufferSize:0x00180000
(II) SAVAGE(0): [junkers] depthOffset:0x00500000
(II) SAVAGE(0): [junkers] textureOffset:0x00680000
(II) SAVAGE(0): [junkers] textureSize:0x00140000
(II) SAVAGE(0): [junkers] logTextureGranularity:0x00000011
(II) SAVAGE(0): [junkers] agpTextureHandle:0x40200000
(II) SAVAGE(0): [junkers] agpTextureSize:0x00e00000
(II) SAVAGE(0): [junkers] logAgpTextureGranularity:0x00000014
(II) SAVAGE(0): [junkers] apertureHandle:0xf2000000
(II) SAVAGE(0): [junkers] apertureSize:0x05000000
(II) SAVAGE(0): [junkers] aperturePitch:0x00002000
(II) SAVAGE(0): [junkers] statusHandle:0x0faea000
(II) SAVAGE(0): [junkers] statusSize:0x00001000
(II) SAVAGE(0): [junkers] sarea_priv_offset:0x00000898
(II) SAVAGE(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: Loaded and initialized /usr/lib/dri/savage_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 2.0.99
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 0.15.2
Module class: X.Org XInput Driver
ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(**) Option "Device" "/dev/input/event6"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event5"
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device HID 1241:1111
(**) HID 1241:1111: always reports core events
(**) HID 1241:1111: Device: "/dev/input/event2"
(II) HID 1241:1111: Found x and y relative axes
(II) HID 1241:1111: Found 3 mouse buttons
(II) HID 1241:1111: Configuring as mouse
(II) XINPUT: Adding extended input device "HID 1241:1111" (type: MOUSE)
(**) HID 1241:1111: YAxisMapping: buttons 4 and 5
(**) HID 1241:1111: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Sony Vaio Keys
(**) Sony Vaio Keys: always reports core events
(**) Sony Vaio Keys: Device: "/dev/input/event7"
(II) Sony Vaio Keys: Found keys
(II) Sony Vaio Keys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Sony Vaio Keys: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Sony Vaio Keys: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Sony Vaio Keys: xkb_layout: "us"
``` 
it will look like this..I'm looking at your post ..I'll be back

---

### Post by forestwalkerjoe on 2009-02-09
ok.. i was trying to do as you suggested.. i could not for th e life of me find a "POUND" sign.. i did find a quote sign.. i think when i am editing it doesnt have a "POUND SIGN". FUNNY.. now that i am replying it see a "#" up there. 
either way i put the LOG into a box like a quote and that should help. 
Some one else also answered me on the other Thread.. they all seem to think it is hopeless unless i use only the VESA Generic thing. 
i followed their idea.. adding a Driver "vesa" to the Edit config thing they asked me to do in command line. 
it asks for a reboot after.. and YES i did get right back in.. with a resolution that is very large.. and can not seemingly be changed.. and all the items that require 3d either DO not run or run so slowly as to not seem to really run either way. 
WHAT seems odd to me.. is : one out of every 8 to 10 times i try and log in.. with Savage card.. i DO get in.. and then all works very well. 
it seems to tell me that once the OS see's what is needed in a Correct way.. all is well. BUT some thing is some how NOT telling it the right thing.. or some how accessing a default over than this VESA or XORG config that does work. IF that is true or if what i said sounds even plausible.. bare with the guy who knows nothing of how this OS really works on a Start up.. then.. i would think that the trouble would really be.. when does the OS tell it self where to look or where is the folder that its telling it to look for? i was told that my HOME FILE doesn't like to mount..If that is true.. and the Savage thing is IN the home folder.. " i have no idea how to check that out or even how to move it if it were" then.. it might not see that set of requirements and therefore NOT load a driver for the vid screen. Is there a way for me to explore that idea? WORKS when it WORKS.. doesnt because of WHAT? 
HONESTLY.. this VESA.. is not great.. and i really like the UBUNTU SYSTEM when it DOES let me in on the Savage Card. its smooth, fast.. clean.. nice resolution and the games i do have and APPS move quickly. 
thanks for your time and consideration of my issue. 

FWJ

---

### Post by redroad55 on 2009-02-09
Verify how much ram is present in bios .. check out these links..[https://help.ubuntu.com/community/SonyVaioBrightness]("https://help.ubuntu.com/community/SonyVaioBrightness")
 [https://wiki.ubuntu.com/LaptopTestingTeam/Sony]("https://wiki.ubuntu.com/LaptopTestingTeam/Sony")
 ```
UBUNTU FAMILY 8.10+ USERS ONLY


LAPTOP TOUCHPAD

Using a laptop? If your cursor shoots off all over the place when you type and seemingly clicks on things without your consent, have no fear, you can disable it's click function while typing in a few simple steps. First of all, execute the following command in the terminal:

gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

Next, copy and paste the following text into the empty document:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="input.x11_driver" string="synaptics">
<merge key="input.x11_options.SHMConfig" type="string">True</merge>
</match>
</device>
</deviceinfo>

Ubuntu/Xubuntu Users: Navigate to "System > Preferences > Sessions" ("Applications > Settings > Autostart Applications" in Xubuntu) and click on "Add". Name it something like "Touchpad Syndaemon", the description can be "Disables touchpad while typing", and the all important command you need is "syndaemon -i 1 -d -t -K". For it to take effect, either logout or reboot.

Kubuntu Users: Create a text document in your home directory called "syndaemon", then open it with a text editor and add the following lines to it:

#!/bin/sh
syndaemon -i 1 -d -t -K

Close and save the file, then move it to the autostart folder with:

mv syndaemon ~/.kde/Autostart

Finally, make the file an executable script with the following command:

chmod u+x ~/.kde/Autostart/syndaemon

Why isn't it enabled by default for laptop users? Well, it's insecure. If you share your laptop with mean geeks, they could disable your touchpad.


PRE-UBUNTU FAMILY 8.10 USERS ONLY


LAPTOP TOUCHPAD

Using a laptop? If your cursor shoots off all over the place when you type and seemingly clicks on things without your consent, have no fear, you can disable it's click function while you're typing by opening your terminal and (carefully) doing the following:

gksudo gedit /etc/X11/xorg.conf

Next, find the section concerning your touchpad and copy the bold text below into your Xorg configuration file, so it looks similar to the example below:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "SHMConfig" "true"
EndSection

Make sure it all looks okay and that the "EndSection" text is in the right place, then close and save.

Ubuntu/Xubuntu Users: Navigate to "System > Preferences > Sessions" ("Applications > Settings > Autostart Applications" in Xubuntu) and click on "Add". Name it something like "Touchpad Syndaemon", the description can be "Disables touchpad while typing", and the all important command you need is "syndaemon -i 1 -d -t -K". For it to take effect, either logout or reboot.

Kubuntu: Create a text document in your home directory called "syndaemon", then open it with a text editor and add the following lines to it:

#!/bin/sh
syndaemon -i 1 -d -t -K

Close and save the file, then move it to the autostart folder with:

mv syndaemon ~/.kde/Autostart

Finally, make the file an executable script with the following command:

chmod u+x ~/.kde/Autostart/syndaemon

Why isn't it enabled by default for laptop users? Well, it's insecure. If you share your laptop with mean geeks, they could disable your touchpad.

``` Some of these things may or may not apply to your situation but it is important to eliminate them before we go on.. Post back

---

### Post by forestwalkerjoe on 2009-02-10
well, here is what i have gathered. ONE.. 
My laptop is not one tested by the synaptic thing. 
its a PCG-XG39K Viao. 
and i have done my best.. and even got an error or two trying to APT GET That app you were writing about.. i finaly did get it to load and all.. i have tried more than once.. so here is the output of that TRY. 
FWJ



```
rj@rj-laptop:~$ grep -E "^sonypi" /proc/modules
sonypi 26648 0 - Live 0xd0d1b000
rj@rj-laptop:~$ sudo modprobe sonypi
rj@rj-laptop:~$ sudo spicctrl
Sony Vaio SPIC control program version 1.9, Jun 28, 2005

Usage: spicctrl [COMMAND] [OPTION]...

Commands:
	-a, --getacstatus		get AC adaptor status
	-b, --setbrightness=NUM		set lcd screen brightness (0-255)
	-B, --getbrightness		get lcd screen brightness
	-c, --getbat1capacity		get first battery capacity
	-C, --getbat2capacity		get second battery capacity
	-l, --setbluetoothpower=NUM	set bluetooth device power state (0-1)
	-L, --getbluetoothpower		get bluetooth device power state
	-p, --powerstatus		print out battery summary
	-r, --getbat1remaining		get first battery remaining capacity
	-R, --getbat2remaining		get second battery remaining capacity
	-s, --getbat1status		get first battery status
	-S, --getbat2status		get second battery status
	-f, --setfanspeed=NUM		set fan speed (0-255)
	-F, --getfanspeed		get fan speed
	-T, --gettemperature		get temperature
rj@rj-laptop:~$ sudospicctrol -B
bash: sudospicctrol: command not found
rj@rj-laptop:~$ sudo echo 4 > /proc/acpi/sony/brightness
bash: /proc/acpi/sony/brightness: No such file or directory
rj@rj-laptop:~$ 

```

I do have a bit of a guess on part of this.. i was told by another person.. that the HOME area on my partition is not loading right.. it was even suggested i move HOME INTO ROOT.. .if the data is being kept there.. and it fails to load.. that might be what is cuasing the confusion in the spicctrl thing.

oh to add to the confusion here is the code to stop the touch pad.. and what happend here too. 

> rj@rj-laptop:~$ mv syndaemon ~/.kde/Autostart
mv: cannot stat `syndaemon': No such file or directory
rj@rj-laptop:~$ chmod u+x ~/.kde/Autostart/syndaemon
chmod: cannot access `/home/rj/.kde/Autostart/syndaemon': No such file or directory
rj@rj-laptop:~$ 

---

### Post by forestwalkerjoe on 2009-02-10
I have been having trouble accessing the BIOS part at boot up. none of the F keys seems to allow me access.. it just black screens till linux grup thing starts. 

i found some stuff on the net that DID seem to help me answer the questions.. IF i have this right.. but its VERY LONG.. so.. i have posted what i see.. and hopefully you are able to help me from there. 

 ```
rj@rj-laptop:~$ sudo lshw
[sudo] password for rj: 
rj-laptop                 
    description: Computer
    product: PCG-XG39K(UC)
    vendor: Sony Corporation
    version: REFURB
    serial: 28316730-3300199
    width: 32 bits
    capabilities: smbios-2.1 dmi-2.1
  *-core
       description: Motherboard
       product: PCG-XG39K(UC)
       vendor: Sony Corporation
       physical id: 0
       version: REFURB
       serial: 28316730-3300199
       slot: &#65533;&#65533;@
[B]     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0205A1 (09/19/00)
          size: 84KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing acpi usb agp ieee1394boot smartbattery netboot[/B]
     *-cpu[B]
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.6
          slot: MMO Con1
          size: 850MHz
          width: 32 bits[/B]
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 32KiB
             capacity: 512KiB
             capabilities: burst external write-back
        *-cache:1
             description: L2 cache
             physical id: 0
             size: 256KiB
     *-cache
          description: L1 cache
          physical id: 9
          slot: L1 Cache
          size: 16KiB
          capacity: 16KiB
          capabilities: asynchronous internal write-back
     [B]*-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 256MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: J28
             size: 128MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: J24
             size: 128MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: J31[/B]
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=64 module=intel_agp
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           [B]*-display UNCLAIMED
                description: VGA compatible controller
                product: 86C270-294 Savage/IX-MV
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 11
                width: 32 bits
                clock: 66MHz[/B]
                capabilities: pm agp agp-1.0 bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=4
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02

             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64 module=ata_piix
  [B][COLOR="Red"]         *-disk
                description: ATA Disk
                product: IBM-DJSA-230
                vendor: IBM
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: JS6O
                serial: 46V46M46169
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=96819681
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 1459-1bd1
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 16GiB
                   capacity: 16GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 7999MiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2124MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 6482MiB[/COLOR][/B]
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-C2402
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1515
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-firewire
             description: FireWire (IEEE 1394)
             product: CXD3222 i.LINK Controller
             vendor: Sony Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=4 module=ohci1394
        *-multimedia
             description: Multimedia audio controller
             product: YMF-744B [DS-1S Audio Controller]
             vendor: Yamaha Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Yamaha DS-1 PCI latency=64 maxlatency=25 mingnt=5 module=snd_ymfpci
        *-communication UNCLAIMED
             description: Communication controller
             product: HCF 56k Data/Fax Modem
             vendor: Rockwell International
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=64
        *-pcmcia:0
             description: CardBus bridge
             product: RL5c478
             vendor: Ricoh Co Ltd
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 80
             width: 64 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
             resources: iomemory:b00502000-b00501fff
        *-pcmcia:1
             description: CardBus bridge
             product: RL5c478
             vendor: Ricoh Co Ltd
             physical id: c.1
             bus info: pci@0000:00:0c.1
             version: 80
             width: 64 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
             resources: iomemory:b00906000-b00905fff
           *-network
                description: Ethernet
                vendor: PCMCIA
                physical id: 0
                slot: Socket 1
                resources: irq:3
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:80:c6:f6:91:9c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=pcnet_cs ip=192.168.1.33 multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:a9:e8:40:52:75
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
rj@rj-laptop:~$ 

```[http://i152.photobucket.com/albums/s196/forestwalkerjoe/Gparted.png]("http://i152.photobucket.com/albums/s196/forestwalkerjoe/Gparted.png")this is the GParted image.. "IF" it lets me share the image that way.. it was too large to post as was.

---

### Post by redroad55 on 2009-02-10
On the first page last post screen shot this is a good partition  breakdown if thats what you went with.. except like was said the
/dev/sda7 the mount point should be /home .. As far as the ram goes ..you have three slots with 128mb in slot 0 and 128mb in slot 1 128mb ..256mb total that's really asking alot of your laptop .. on the bios access go to sony's web site and read or copy any documentation you can get there on your machine it will show you about the f keys and which one opens your bios .. You really need some more ram and sony's documentation will tell you what kind and what is max for your machine.. You can probably buy 3 sticks of 256mb for $5.00 to $8.00 a stick plus shipping on ebay and it would help you out alot .. I wil talk to you tomorrow with more .. until then .. Best to you

---

### Post by forestwalkerjoe on 2009-02-11
i did some guessing when i designed that partition set up. I was really not so sure how to do it.. or what needed to be where. If i have you right.. you are saying that the SDA7 needs to be changed in the Gpart to list as HOME? is this why i am told the HOME folder is not mounting? 
i am still learning here and i don't want to seem dim. 
i have had another person trying to help me re size my set up in Gpart.. but over a week ago i stopped to deal with the more immediate issue of Black Screen.. His last comments are awkward to me.. i am concerned that if i do what he has asked.. it might change things so that other work WONT be able to find its connections. 
I am not sure if that made sense or if you understand why i would even say that. 

here is the [LINK]("http://ubuntuforums.org/showthread.php?t=1060041&page=2") to his postings.. i will not attempt those untill i am sure all is up and running.. and that doing so wont mess up every thing. 
as to RAM. i know that ram sticks are different for each type of machine.. i have no real way of understanding what kind these are.. or how to order those.. once i am sure i have the right thing to ask for.. i CAN order more ram on Ebay as you suggested. BIOS is a matter of [hitting F2]("http://www.michaelstevenstech.com/bios_manufacturer.htm") upon rebooting. BUT.. as i said.. HITTING F2 stopped working after i installed UBUNTU. i don't know if this was because Grub got in the way or if there isn't enough time in the echo thing for it to allow it? or what. 
(edit) after messing around with a couple configurations I finally did get into the BIOS. 
BUT i am not sure if i understand what you are asking me. the line up for Ram in here says. 
I have TOTAL 256 ram. expandable. 
8 Mgs video ram. I think that is the part you are asking about? I am not sure what the differences are.. just that SDRAM or other types.. don't fit in every machine the same way. they have different slots. SO i guess i can unscrew the bottom.. look at these.. and hopefully find the right type of ram sticks.. and then order them On e-bay. 
I am hoping that we can still Do work in the mean time.. as that might take a heck of a while to get here.. in comparison to my Goals to fix MINE and Friends PC. Maybe in a month.. I'll go a hunting for a replacement battery for this beast.. its been running on Plug in for a long while and the duel battery slots have ONE in it.. but its long past dead. Doesn't even try and charge any more. This was only  a back up.. mess around lappy.. its becoming a helper / learning tool now. thanks for helping me do that. 
there have been other things going on.. such as this below here.  

here is the link to the guys postings on [RESIZING in GPART.]("http://ubuntuforums.org/showthread.php?t=1060041&page=2") 
I have to head off to work.. has a grave yard shift and no net connection. 
again thanks for helping me get all this working. 

FWJ

---

### Post by forestwalkerjoe on 2009-02-11
Ok.. i opened the G-parted again.. and i am looking over the options.. most of which i "THINK" i understand. 
When you say.. /dev/sda7 - the mount point should be / home.. or " Root Home" .. right? I have no idea how to change that.. and it does have 256 mgs used on that part. I have not the first clue how to change that. I know i can RESIZE It.. but any other thing seems to be used to format it. when i right click on the SDA7 it sounds Unmounted. I have NO idea how to Mount that either. I know you think that i have some things I understand.. but honestly.. i was not using Linux for more than a year.. and when i did use Linux for the year before.. i was working with 8 versions. 8 versions with a lot of helps from Forums. at that time i could recall a lot of things.. now.. i am in many ways.. starting all over again. JUST.. with ONLY Ubuntu.. and no ideas of trying out any others any time soon. I want to learn this one. 
As to the codes that the other guy gave me.. i want to make sure i underand exactly what the affects will be if i Do the changes he is suggesting. So that.. IF you and I are working on some thing.. and we find a possible solve for some of the issues we have been discussing.. changing where things are.. doesnt change the playing field in a bad way.. before or after i work with his code. Speaking of code.. there are two options i have been discussing with him. ONE is : not only the idea of resizing these parts.. so that every thing is in a good optimal place.. but size. TWO: it was the debate on wheather i need to have one of these parts. the thinking was.. moving or not moving HOME into the ROOT. Its been said that having a home folder is a great idea.. because IF i have to do some sort of reinstall.. most of the stuff i use would have been INSIDE of HOME and could all be fixed fast if its NOT inside root. Yet.. there is always.. the fact that my SDA7 is large.. and this is ONLY a 30 gig drive. part of which is dedicated to the Win2k Fat partition. 
What are you thoughts on these ? 
I do think I'd like to take the windows part and resize it smaller... but i am also concerned if i were To do that.. would it just take that space and leave an unformated space between..windows and LINUX Root? 
All these are just a matter of understanding HOW these things work.. time and experiences would make it easier to do later.
OH.. and how is it i have the first two partitions listed as SDA1 and 2.. but every thing else after that.. is listing from numbers 5,6 and 7 ? 
where are the other numbers?

---

### Post by redroad55 on 2009-02-11
My best advice at this point is to do a fresh install .. as to the numerical assignments .. all primary partitions are numbered 1-4 and logical partitions 5-8 .. The partition screen shot you made is a good size lay out for your drive and placement of the partitions is good aside from sda 7  mount point being /home .. the reason I say fresh install is you have made many changes some with success and some not leaving your OS in a confused state .. To debug Sure its possible ... But it is a futile process here for you and those that want to help you when you try to work om more than one thing at a time .. Besides you have expressed your desire to learn this process in a way that would allow you to do it on other machines .. The most important initial step is being able to partition a dual boot drive and be comfortable as well as familiar enough with the process so you can repeat the process .. You have more to learn about how to do this manually .. We have all started where you are at in order to learn .. Where we learn the most is when we make a mistake and learn from it .. Post back any thoughts or questions >> best to you

---

### Post by redroad55 on 2009-02-11
In looking back thru your post I see this :
> Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
is this the kernel you have installed??

you definitely want the I386 version ...Here is the link to get that:
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
 Post back

---

### Post by forestwalkerjoe on 2009-02-11
Ok early on in my postings in here.. i had several troubles.. one i had an odd PCMICI Ether Card.. it took quite a bit to get that running.. 
and then there was a problem with Kernel panic if i chose the recent installed ubuntu. BUT becuase i had been runing from live CD then had a strange install.. i had two kernels choices. 
#title		Ubuntu 8.10, kernel 2.6.27-11-generic
#uuid		#4e1de464-d3c7-4be0-9430-474ebfcc3f83
#kernel		#/boot/vmlinuz-2.6.27-11-generic root=UUID=4e1de464-d3c7-4be0-9430-474ebfcc3f83 ro quiet splash 
#initrd		#/boot/initrd.img-2.6.27-11-generic
#quiet

Which later i did edit to NOT show this one in Grub.. becuase it would freeze and then not  start up. 
then there is the one i have been using. 

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4e1de464-d3c7-4be0-9430-474ebfcc3f83
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4e1de464-d3c7-4be0-9430-474ebfcc3f83 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

I am still not sure why the kernel would panic every time i chose the first one. BUT the 27-07 worked. 
I am not sure if these are related to what you are saying.. or not.. but if you wish i can try and un comment the version 11 one.. and see if that will somehow now load. 

I am loath to uninstall reinstall. It was a pain to get it all in here. there must be a way to just make changes to what is here. 

FWJ 

CPU=i686,
Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008
scanModem update of: 2009_01_19

---

### Post by redroad55 on 2009-02-11
In order to get all hardware supported on initial install the appropriate kernel is crucial .. So what kernel did you install and did you put the image on cd or how did you install ? If you are wanting to replicate and or show someone else how to do that than what I am asking you is all totally relevant information in helping you accomplish that .. Post back

---

### Post by forestwalkerjoe on 2009-02-11
i again tried to un comment the version 11 one.. and it would fail based off file not found.. or the recovery version.. would just reboot. so i have commented them out again. 
My install came from a DISK i ordered on Ebay of version 8.10 Ibix. i still have that CD. 
i would have to go back out there and find exactly what Pythias had me do.. to get the right drivers and so on set up.. so that this Very old PCMICIA Ether Card would work again.. there was so much i couldn't do until that was fixed. there were also other little things that had to be done to make things work. I would need to back up some files.. so that i dont loose them. Since some things are in the system now.. can those be backed up into a HOME styled file? then reinstalled from there to the new install you are intending me to do ?

---

### Post by redroad55 on 2009-02-11
If you have a cd burner you can transfer files that way.. Might be best ... Next If you have a way to download the image on the link I listed above and put it on cd .. It will be what you need for any desktop or laptop that has a 32 bit processor... Let me know

---

### Post by forestwalkerjoe on 2009-02-11
i don't have a burner on this laptop.. what i dont understand is i have the ibix version810 of ubuntu.. why is that one not correct for this install? 
why are you having me do another style of Ubuntu?
None the less.. i am doing a bit of back up for every thing.. and i am going to search out all the CODES I was given.. so that i can re establish the PCMCIA NIK2 card i have.. and find the proper installs for the DVD player .. which took time.. and i have made a list of the programs i had already installed and were using. 
ONCE i am confident i can do all that.. then .. i need to figure out how to download and install this Other version you are talking about.. with some sort of ISO creator or burner for the DeskTOP. ONCE i have this all together.. with a little help.. i'll be glad to look at your notes for a Reinstall. 
I have windows 2k on this primary.. and dont have good reinstall disks for that.. so i have to leave that alone. I will even back up part of that install so that there is more space and such to resize the drive. 
If what you seem to be suggesting is true.. we are going to do a rebuild of the system.. other than win2k.. from ground up.. so that all works the WAY it really should.. i am cool with that. I am actually very cool with that. As long as you can see that the hardware will be upgraded.. as i have money.. for now.. RAM will have to wait.. not long , but no money is no money.. once i CAN do it.. the ram will just make life easier. 
then.. battery.. and so forth. 

Write me back..

---


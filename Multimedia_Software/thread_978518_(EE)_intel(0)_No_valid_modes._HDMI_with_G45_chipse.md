---
title: "(EE) intel(0): No valid modes. HDMI with G45 chipset"
date: 2008-11-11
forum: Multimedia Software
---

### Post by rdlenny on 2008-11-11
Hi,

I have recently purchased a new Intel DG45ID motherboard and have seen that some people have had success with Ubuntu 8.10 with these boards. Having tried this myself Xserver won't start with the intel driver and only loads using the Vesa driver under the failsafe config.

I'm using the onboard HDMI interface connecting to a Sony X series LCD TV. Hopefully this is only a gumby Xorg config error on my part, but although finding many similar problems and error messages in searching various forums I haven't found anything that exactly fits the problem I'm seeing. The DG45ID uses a G45 chipset, I think the exact graphics device used is known as an X4500HD. Here is the lspci, Xorg log and xorg.conf files for my system:

lspci:

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LF-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

Xorg.0.log:

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux mediacentre 2.6.27-8-generic #1 SMP Thu Nov 6 17:33:54 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 11 17:11:32 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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

(--) PCI:*(0@0:2:0) Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xff000000/0, 0xc0000000/0, I/O @ 0x0000f1c0/0
(--) PCI: (0@0:2:1) Intel Corporation 4 Series Chipset Integrated Graphics Controller rev 3, Mem @ 0xff400000/0
(--) PCI: (0@1:0:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xd0001000/0
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 2.4.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33,
        Mobile IntelÂ® GM45 Express Chipset,
        Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.1.0
        ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G45/G43
(--) intel(0): Chipset: "G45/G43"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xFF000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 32704 kB
(II) intel(0): VESA VBE OEM: Intel(r)Eaglelake Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)Eaglelake Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): Output HDMI-1 has no monitor section
(II) intel(0): I2C bus "HDMIDDC_B" initialized.
(II) intel(0): HDMI output 1 detected
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output HDMI-2 has no monitor section
(II) intel(0): I2C bus "HDMIDDC_C" initialized.
(II) intel(0): HDMI output 2 detected
(II) intel(0): Output VGA disconnected
(II) intel(0): Output HDMI-1 disconnected
(II) intel(0): Output HDMI-2 disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(II) intel(0): Output HDMI-1 disconnected
(II) intel(0): Output HDMI-2 disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

xorg.conf:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

I have upgraded my Kernel to 2.6.27-8-generic from packages. I hope someone with some Ubuntu and Xorg experience can help.

Regards,


Richard

---

### Post by MTisza on 2008-12-20
Unfortunately I can't offer any help, but I can confirm the exact same issue with my ASUS P5Q-EM motherboard, which has the G45 chipset.  I get the same issue with both 32 and 64 bit live CD's and even after installing to HD.  Did you ever resolve this?

I have tried many things.  I can use get-edid successfully, so I doubt this is a hardware issue.  I tried hard coding the edid in the xorg.conf file with the CustomEDID option.  I tried the latest intel drivers 2.5.1 from a ppa.  The normal action of ubuntu is to say it will run in low graphic mode, and after confirming this X uses the vesa driver which is fully able to detect the EDID of the monitor over the HDMI DDC (this was verified in the xorg log).

When using the vesa driver things are good enough for me, since I don't use any fancy graphics, normally.  The resolution ends up being the full native res of the monitor (1680x1050 or so).  However I would really like to setup mythbuntu and this is the only setback.

---

### Post by maxim99 on 2008-12-26
I am in the same boat as you. I have my machine hooked up to a projector and it won't always be on when it starts up. So I need X to load up when there is not necessarily a monitor hooked up to it.

---

### Post by maxim99 on 2008-12-27
This appears to be an issue with the Intel driver itself. This bug here:

[https://bugs.freedesktop.org/show_bug.cgi?id=14611](https://bugs.freedesktop.org/show_bug.cgi?id=14611)

This explains the situation exactly. One of the developers proposes a possible patch for it. I hope that this makes it's way into the stable driver release as I don't know the the first thing about compiling a driver.

---

### Post by maxim99 on 2008-12-27
Using Jaunty (9.04 Alpha2), I did not encounter this issue. Seems the new driver version has addressed this issue and picks an output anyway. NICE!

---

### Post by MTisza on 2008-12-27
> **maxim99 said:**
> Using Jaunty (9.04 Alpha2), I did not encounter this issue. Seems the new driver version has addressed this issue and picks an output anyway. NICE!

Interesting.  I've tried Jaunty Alpha2 and had no difference. I'll give it another try soon.  Did you have to do anything special?  Which version are you using 32-bit or 64-bit?

---

### Post by ghat on 2009-03-21
> **MTisza said:**
> Unfortunately I can't offer any help, but I can confirm the exact same issue with my ASUS P5Q-EM motherboard, which has the G45 chipset.  I get the same issue with both 32 and 64 bit live CD's and even after installing to HD.  Did you ever resolve this?

I have tried many things.  I can use get-edid successfully, so I doubt this is a hardware issue.  I tried hard coding the edid in the xorg.conf file with the CustomEDID option.  I tried the latest intel drivers 2.5.1 from a ppa.  The normal action of ubuntu is to say it will run in low graphic mode, and after confirming this X uses the vesa driver which is fully able to detect the EDID of the monitor over the HDMI DDC (this was verified in the xorg log).

When using the vesa driver things are good enough for me, since I don't use any fancy graphics, normally.  The resolution ends up being the full native res of the monitor (1680x1050 or so).  However I would really like to setup mythbuntu and this is the only setback.


CustomEDID: I think thats an Nvidia only driver option, not intel...

---


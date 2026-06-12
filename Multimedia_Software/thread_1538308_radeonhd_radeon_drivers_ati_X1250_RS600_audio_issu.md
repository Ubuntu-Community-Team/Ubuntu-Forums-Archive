---
title: "radeonhd radeon drivers ati X1250 RS600 audio issues"
date: 2010-07-24
forum: Multimedia Software
---

### Post by tjones00 on 2010-07-24
Hi I was wondering if anybody could help me setting up audio over a ATI X1250 RS600 base in ubuntu 10.04. Abit Fatal1ty F-I90HD motherboard.

I'm at my wits end. I'm one of those people that got the door slammed in their face by ATI.

My goal is to get audio as well as video over my hdmi cable. Right now I can only get video.

Things I've tried.

Updating the kernel to 2.6.34-rc 4, and rc7, as well as 2.6.35-rc1 to get the basic radeon driver as well as the edge drivers to work. Resulted in nothing. Edge bugged out pretty good on the newer lucid kernels btw stay away from them if you use those.

I can install radeonhd and get audio working with the default 2.6.32 kernel when I restart X however if I reboot the system xserver fails when it tries to init which is odd. Which makes me think even though they say you can turn off kms you really can't.

Disabling kms via grub nomodeset as well as the method listed on the ubuntu wiki kernelmodesetting page.

I've also tried noplymouth but it still results in the same effect.

My Xorg.log usuallysays something about power mode or atombios when failing. I've set ForceLowPowerMode but I can't get a full stable x under radeonhd now to do a Xorg -configure and get all the options. (it requires a successful Xorg.log). I can't get it running again after the first time I restarted X.

I also ensured my audio wasen't muted in alsa.

I was wondering if anybody could point me somewhere where I could get info about successfully using the radeonhd driver with 10.04. The ubuntu wiki is pretty much worthless for this issue. Kernelmodesetting page tells you to use /usr/lib/X11/xorg.conf.d/whatever.conf to switch a driver whereas other pages tell you to do the generic /etc/X11/xorg.conf. Both result in the same failures.

I can't use ati prop driver higher than 9.3 with 5yr old hardware :| The xserver in 10.04 requires a newer ati driver.
The open source radeon driver fails on hdmi audio for RS600 even with updated kernels and drivers

So I'm stuck with the radeonhd driver. Anyway any info would be appreciated.

---

### Post by Mark Phelps on 2010-07-25
Wish you luck, but I've read several places that support has been dropped for the radeonhd driver.

You could try checking over at the Phoronix forum in their open source ATI drivers subforum.  There may be posts there dealing with detail settings using the radeonhd driver.

---

### Post by tjones00 on 2010-07-25
Thank you I definately will check it out.

As to my own progress I had a breakthrough last night after I posted here.

The Xorg.log errors I was getting pointed me to AtomBIOS being the issue. So from an old xorg.conf I gathered from a successful session log I was able to probe all the variables on the radeonhd driver currently in the lucid repo. 

On of them was UseAtomBIOS so I added that option as well as ForceLowPowerMode

Option     "UseAtomBIOS"  "False"
Option      "ForceLowPowerMode"  "True"

After that It still failed to boot with the same errors and the log showed that it was still trying to probe the bios.

So I handed the probing back over the kms turning it back on since some kms work has been done on the radeonhd driver and kept plymouth disabled.

Success.

I've saved my logs and xorg.conf from the old system and am trying to replicate the results now with a fresh install.

If I can replicate my success I'll post a working /etc/X11/xorg.conf, /var/log/Xorg.log, and /etc/default/grub here. I'll also post all the radeonhd options.

---

### Post by tjones00 on 2010-07-27
Well that was a waste of a week.

I can get it running but only with 2d support. Apparently my card is not recognized in the default AtomBIOS library and the AtomBIOS it tries to use breaks any hope of 3d or even Xv rendering. I cannot disable AtomBIOS. I really don't feel like compiling the driver myself. I guess I could try.

This will not do since I'm trying to establish a XBMC / server.

Anyway I can still enable my analog sound or run a spdif cable to the tv and use the radeon driver.

It might still work for some people so here is what I gathered.

The radeonhd driver doesn't play nice with xrandr that is probably why I had to disable plymouth in order to get to the gdm login. 

Results from only having 1 display a 720p lcd TV connected.


using the default radeon driver

```
pinker@pinker-MPC:~$ sudo xrandr
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1280x720+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1280x720       60.0*+
   720x480        59.9  
   640x480        60.0  
```using default radeonhd

```
pinker@pinker-MPC:~$ sudo xrandr
Screen 0: minimum 320 x 200, current 640 x 480, maximum 3840 x 1920
VGA_1 connected 640x480+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      75.0     59.9     60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     66.7     60.0* 
   720x400        70.1  
TV_SVIDEO disconnected (normal left inverted right x axis y axis)
DVI-D_1 disconnected (normal left inverted right x axis y axis)
DVI-D_2 connected 640x480+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1280x720       60.0 +
   640x480        60.0* 
```This would force a 640x480 display since the driver thought 2 displays were active and it used the only compatible resolution for both.

xrandr --output VGA_1 --off and xrandr --auto did not fix this issue.

I also played around with the HPD driver option but this did not fix the issue.

Enabling the driver option  "Norandr" fixed this issue.

```
pinker@pinker-MPC:~$ sudo xrandr
Screen 0: minimum 640 x 480, current 1280 x 720, maximum 1280 x 720
default connected 1280x720+0+0 0mm x 0mm
   1280x720       60.0* 
   640x480        60.0 
```The next issue was no 3d acceleration.
```

pinker@pinker-MPC:~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
```DRI and EXA are enabled and mesa is installed this is where I think the improper AtomBIOS comes in and messes everything up.
 
xorg.0.log.old
line 458
(II) RADEONHD(0): Query for AtomBIOS Get Datatable from Codetable: failed
None
(II) RADEONHD(0): RHDAudioSetClock: using TMDS B as clock source with 74250 khz
(II) RADEONHD(0): Using ACR timing N=4096 CTS=74250 for frequency 32000
(II) RADEONHD(0): Using ACR timing N=6272 CTS=82500 for frequency 44100
(II) RADEONHD(0): Using ACR timing N=6144 CTS=74250 for frequency 48000
(II) RADEONHD(0): RHDAudioSetSupported: config 0x60040 codec 0x1
(II) RADEONHD(0): Using HW cursor
(==) RADEONHD(0): DPMS enabled
(II) RADEONHD(0): Xv: No Textured Video possible without the Command Processor.

full log

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux pinker-MPC 2.6.32-24-generic-pae #38-Ubuntu SMP Mon Jul 5 10:54:21 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=83ea8418-7490-40e1-9b25-c66f44a17225 ro noplymouth
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 27 09:07:50 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
(**) |   |-->Device "Configured Video Device"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:5:0) 1002:7941:1002:7941 ATI Technologies Inc RS600 [Radeon Xpress 1200 Series] rev 0, Mem @ 0xd0000000/268435456, 0xfdfe0000/65536, I/O @ 0x0000de00/256
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "radeonhd"
(II) Loading /usr/lib/xorg/modules/drivers/radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
    compiled for 1.7.3.902, module version = 1.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
    RV505 : Radeon X1550, X1550 64bit.
    RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
    RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
    R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
    RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
    RV535 : Radeon X1300, X1650.
    RV550 : Radeon X2300 HD.
    RV560 : Radeon X1650.
    RV570 : Radeon X1950, X1950 GT; FireGL V7400.
    R580  : Radeon X1900, X1950; AMD Stream Processor.
    R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
    RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
    RV620 : Radeon HD 3450, HD 3470.
    RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
        FireGL V3600/V5600.
    RV635 : Radeon HD 3650, HD 3670.
    RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
    R680  : Radeon HD 3870 X2.
    M52   : Mobility Radeon X1300.
    M54   : Mobility Radeon X1400; M54-GL.
    M56   : Mobility Radeon X1600; Mobility FireGL V5200.
    M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
    M62   : Mobility Radeon X1350.
    M64   : Mobility Radeon X1450, X2300.
    M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
    M68   : Mobility Radeon X1900.
    M71   : Mobility Radeon HD 2300.
    M72   : Mobility Radeon HD 2400; Radeon E2400.
    M74   : Mobility Radeon HD 2400 XT.
    M76   : Mobility Radeon HD 2600;
        (Gemini ATI) Mobility Radeon HD 2600 XT.
    M82   : Mobility Radeon HD 3400.
    M86   : Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700.
    M88   : Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2.
    RS600 : Radeon Xpress 1200, Xpress 1250.
    RS690 : Radeon X1200, X1250, X1270.
    RS740 : RS740, RS740M.
    RS780 : Radeon HD 3100/3200/3300 Series.
    R700  : Radeon R700.
    RV710 : Radeon HD4570, HD4350.
    RV730 : Radeon HD4670, HD4650.
    RV740 : Radeon HD4770. EXPERIMENTAL AND UNTESTED.
    RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
    RV790 : Radeon HD 4890.
    M92   : Mobility Radeon HD4330, HD4530, HD4570. EXPERIMENTAL.
    M93   : Mobility Radeon M93. EXPERIMENTAL AND UNTESTED.
    M96   : Mobility Radeon HD4600.
    M97   : Mobility Radeon HD4860. EXPERIMENTAL AND UNTESTED.
    M98   : Mobility Radeon HD4850, HD4870.

(II) RADEONHD: version 1.3.0, built from dist of git branch master, commit 8cbff7bf

(II) Primary Device is: PCI 01@00:05:0
(II) RADEONHD(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Option "AccelMethod" "EXA"
(**) RADEONHD(0): Option "HPD" "Auto"
(**) RADEONHD(0): Option "NoRandr"
(**) RADEONHD(0): Option "DRI" "on"
(**) RADEONHD(0): Option "Audio" "true"
(**) RADEONHD(0): Option "HDMI" "all"
(**) RADEONHD(0): Selected EXA 2D acceleration.
(II) RADEONHD(0): Card not in database: 0x7941:0x1002:0x7941; using generic modesetting.
    If - and only if - your card does not work or does not work optimally
    please contact radeonhd@opensuse.org to help rectify this.
    Use the subject: 0x7941:0x1002:0x7941: <name of board>
    and *please* describe the problems you are seeing
    in your message.
(--) RADEONHD(0): Detected an RS600 on an unidentified card
(II) RADEONHD(0): Mapped IO @ 0xfdfe0000 to 0xb72c4000 (size 0x00010000)
(II) RADEONHD(0): Getting BIOS copy from legacy VBIOS location
(II) RADEONHD(0): ATOM BIOS Rom: 
    SubsystemVendorID: 0x1002 SubsystemID: 0x7941
    IOBaseAddress: 0xde00
    Filename: S3A70710.016
    BIOS Bootup Message:  
ATI Radeon Xpress 1250 for Marlin w/HDMI                                     

(II) RADEONHD(0): Analog TV Default Mode: 1
(II) RADEONHD(0): Found default TV Mode NTSC
(II) RADEONHD(0): The detected amount of videoram exceeds the PCI BAR aperture.
(II) RADEONHD(0): Using only 262144kB of the total 524288kB.
(--) RADEONHD(0): VideoRAM: 262144 kByte
(II) RADEONHD(0): Framebuffer space used by Firmware (kb): 20
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0x1fffb000
(II) RADEONHD(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0x1fffb000
(WW) RADEONHD(0): rhdAtomAllocateFbScratch: FW FB scratch area 536850432 (size: 20480) extends beyond available framebuffer size 268435456
(II) RADEONHD(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEONHD(0): Default Engine Clock: 500000
(II) RADEONHD(0): Default Memory Clock: 266000
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 14320
(II) RADEONHD(0): Found libdri 5.4.0.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEONHD(0): Found libdrm 1.3.0.
(II) RADEONHD(0): Found radeon drm 2.0.0.
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEONHD(0): Default Engine Clock: 500000
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) RADEONHD(0): Detected VGA mode.
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 14320
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00000000 (size = 0x00004000)
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00004000 (size = 0x00004000)
(II) RADEONHD(0): FirmwareInfo Revision 0104
(II) RADEONHD(0): Unused attribute: ul3DAccelerationEngineClock 0
(II) RADEONHD(0): Unused attribute: ulDriverTargetEngineClock 0
(II) RADEONHD(0): Unused attribute: ulDriverTargetMemoryClock 0
(II) RADEONHD(0): Unused attribute: ucASICMaxTemperature 0
(II) RADEONHD(0): Scary bits: Estimated MinEngineClock 250000 kHz
(II) RADEONHD(0): Scary bits: Estimated MinMemoryClock 250000 kHz
(II) RADEONHD(0): Default Engine Clock: 500000
(II) RADEONHD(0): Default Memory Clock: 266000
(II) RADEONHD(0): Current Engine Clock: 501200
(WW) RADEONHD(0): AtomBIOS command table 47 does not exist
(II) RADEONHD(0): Query for AtomBIOS Exec: not implemented
(WW) RADEONHD(0): Unusupported SetVoltage Revision
(II) RADEONHD(0): Power Management: used engine clock / memory clock / core (VDDC) voltage   (0: ignore)
(II) RADEONHD(0): Power Management: Raw Ranges
(II) RADEONHD(0):   Minimum    250000 kHz /   250000 kHz /  0.000 V
(II) RADEONHD(0):   Maximum         0 kHz /   650290 kHz /  0.000 V
(II) RADEONHD(0):   Default    500000 kHz /   266000 kHz /  0.000 V
(II) RADEONHD(0): PowerPlayInfo Revision 0000
(EE) RADEONHD(0): Unusupported PowerPlayInfo Revision
(II) RADEONHD(0): Query for Get Chip Configs: not implemented
(EE) RADEONHD(0): Power Management: Cannot get known good chip configurations
(II) RADEONHD(0): Power Management: Validated Ranges
(II) RADEONHD(0):   Minimum    250000 kHz /   250000 kHz /  0.000 V
(II) RADEONHD(0):   Maximum    501200 kHz /   650290 kHz /  0.000 V
(II) RADEONHD(0):   Default    500000 kHz /   266000 kHz /  0.000 V
(II) RADEONHD(0): Power Management: Final Levels
(II) RADEONHD(0):   Off        250000 kHz /   250000 kHz /  0.000 V
(II) RADEONHD(0):   Idle       500000 kHz /   266000 kHz /  0.000 V
(II) RADEONHD(0):   Slow2D     500000 kHz /   266000 kHz /  0.000 V
(II) RADEONHD(0):   Fast2D     500000 kHz /   266000 kHz /  0.000 V
(II) RADEONHD(0):   Slow3D     500000 kHz /   266000 kHz /  0.000 V
(II) RADEONHD(0):   Fast3D     500000 kHz /   266000 kHz /  0.000 V
(II) RADEONHD(0):   Max3D      501200 kHz /   650290 kHz /  0.000 V
(II) RADEONHD(0):   User       500000 kHz /   266000 kHz /  0.000 V
(II) RADEONHD(0): Connector[0] {RHD_CONNECTOR_VGA, "VGA CRT1", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[1] {RHD_CONNECTOR_TV, "SVIDEO TV1", RHD_DDC_NONE, RHD_HPD_NONE, { RHD_OUTPUT_DACA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[2] {RHD_CONNECTOR_DVI, "DVI-I DFP2", RHD_DDC_2, RHD_HPD_NONE, { RHD_OUTPUT_LVTMA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[3] {RHD_CONNECTOR_DVI_SINGLE, "HDMI Type A DFP3", RHD_DDC_1, RHD_HPD_NONE, { RHD_OUTPUT_LVTMA, RHD_OUTPUT_NONE } }
(--) RADEONHD(0): Attaching Output DAC A to Connector VGA 1
(--) RADEONHD(0): Attaching Output DAC A to Connector TV SVIDEO
(--) RADEONHD(0): Attaching Output TMDS B to Connector DVI-D 1
(--) RADEONHD(0): Attaching Output TMDS B to Connector DVI-D 2
(II) RADEONHD(0): RandR 1.2 support disabled due to configuration
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): Setting TMDS B to incoherent
(II) RADEONHD(0): Enabling HDMI on DVI-D 1 because of config option
(II) RADEONHD(0): Setting TMDS B to incoherent
(II) RADEONHD(0): Enabling HDMI on DVI-D 2 because of config option
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(WW) RADEONHD(0): Connector "VGA 1": Failed to retrieve Monitor information.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) Quirked EDID physical size to 0x0 cm
(II) RADEONHD(0): EDID data for SAMSUNG
(II) RADEONHD(0): Manufacturer: SAM  Model: 313  Serial#: 0
(II) RADEONHD(0): Year: 2007  Week: 20
(II) RADEONHD(0): EDID Version: 1.3
(II) RADEONHD(0): Digital Display Input
(II) RADEONHD(0): Indeterminate output size
(II) RADEONHD(0): Gamma: 2.40
(II) RADEONHD(0): No DPMS capabilities specified
(II) RADEONHD(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEONHD(0): First detailed timing is preferred mode
(II) RADEONHD(0): redX: 0.632 redY: 0.357   greenX: 0.289 greenY: 0.596
(II) RADEONHD(0): blueX: 0.143 blueY: 0.085   whiteX: 0.280 whiteY: 0.290
(II) RADEONHD(0): Supported established timings:
(II) RADEONHD(0): 640x480@60Hz
(II) RADEONHD(0): Manufacturer's mask: 0
(II) RADEONHD(0): Supported detailed timing:
(II) RADEONHD(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
(II) RADEONHD(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
(II) RADEONHD(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
(II) RADEONHD(0): Supported detailed timing:
(II) RADEONHD(0): clock: 74.2 MHz   Image Size:  160 x 90 mm
(II) RADEONHD(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEONHD(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) RADEONHD(0): Ranges: V min: 59 V max: 61 Hz, H min: 30 H max: 46 kHz, PixClock max 80 MHz
(II) RADEONHD(0): Monitor name: SAMSUNG
(II) RADEONHD(0): Number of EDID sections to follow: 1
(II) RADEONHD(0): EDID (in hex):
(II) RADEONHD(0):     00ffffffffffff004c2d130300000000
(II) RADEONHD(0):     141101038010098c0ae2bda15b4a9824
(II) RADEONHD(0):     15474a20000001010101010101010101
(II) RADEONHD(0):     010101010101011d007251d01e206e28
(II) RADEONHD(0):     5500a05a0000001e011d8018711c1620
(II) RADEONHD(0):     582c2500a05a0000009e000000fd003b
(II) RADEONHD(0):     3d1e2e08000a202020202020000000fc
(II) RADEONHD(0):     0053414d53554e470a202020202001a4
(II) RADEONHD(0): Connector "DVI-D 2" uses Monitor "SAMSUNG":
    Bandwidth: 80MHz
    Horizontal timing:
        30.0 - 46.0kHz
    Vertical timing:
        59.0 - 61.0Hz
    DPI: 203x203
    Allows reduced blanking.
    Attached modes:
        Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
        Modeline "1280x720"   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync
        Modeline "1920x540"   74.25  1920 2008 2052 2200  540 542 547 562 interlace +hsync +vsync
(II) RADEONHD(0): Listing modesetting layout:

    CRTC 1: tied to PLL 1 and LUT A:
        Outputs: DAC A (VGA 1)

    CRTC 2: tied to PLL 2 and LUT B:
        Outputs: TMDS B (DVI-D 2)


(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Validating Modes from Monitor "SAMSUNG" on "DVI-D 2"
(II) RADEONHD(0): Rejected mode "1920x540" (1920x540:74.2Mhz): vrefresh out of range
(II) RADEONHD(0): Using 203x203 DPI.
(II) RADEONHD(0): Using 1280x720 Framebuffer with 1280 pitch
(II) RADEONHD(0): FB: Allocated ScanoutBuffer at offset 0x00008000 (size = 0x00384000)
(--) RADEONHD(0): Virtual size is 1280x720 (pitch 1280)
(**) RADEONHD(0): *Mode "1280x720": 74.2 MHz, 45.0 kHz, 60.0 Hz
(II) RADEONHD(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
(**) RADEONHD(0): *Mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RADEONHD(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.5.0
    ABI class: X.Org Video Driver, version 6.0
(II) RADEONHD(0): FB: Allocated Offscreen Buffer at offset 0x0038C000 (size = 0x01999000)
(II) RADEONHD(0): FB: Allocated DRI Back Buffer at offset 0x01D25000 (size = 0x00384000)
(II) RADEONHD(0): FB: Allocated DRI Depth Buffer at offset 0x020A9000 (size = 0x00384000)
(II) RADEONHD(0): FB: Allocated DRI Textures at offset 0x0242D000 (size = 0x0D800000)
(II) RADEONHD(0): Using 16 MB GART aperture
(II) RADEONHD(0): Using 2 MB for the ring buffer
(II) RADEONHD(0): Using 2 MB for vertex/indirect buffers
(II) RADEONHD(0): Using 12 MB for GART textures
(--) Depth 24 pixmap format is 32 bpp
(II) RADEONHD(0): Mapped IO @ 0xfdfe0000 to 0xb72c4000 (size 0x00010000)
(II) RADEONHD(0): Mapped FB @ 0xd0000000 to 0xa7293000 (size 0x10000000)
(WW) RADEONHD(0): rhdVGASaveFB: Unable to access the VGA framebuffer (0xC0000000)
(II) RADEONHD(0): Attempting to enable power management
(WW) RADEONHD(0): AtomBIOS command table 19 does not exist
(II) RADEONHD(0): Query for AtomBIOS Exec: not implemented
(WW) RADEONHD(0): Failed to set power management
(II) RADEONHD(0): Query for Set Power Management: failed
(II) RADEONHD(0): Attempting to enable clock gating
(II) RADEONHD(0): Current Engine Clock: 501200
(WW) RADEONHD(0): AtomBIOS command table 47 does not exist
(II) RADEONHD(0): Query for AtomBIOS Exec: not implemented
(WW) RADEONHD(0): Unusupported SetVoltage Revision
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEONHD(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEONHD(0): [drm] framebuffer handle = 0xd0000000
(II) RADEONHD(0): [drm] added 1 reserved context for kernel
(II) RADEONHD(0): X context handle = 0x1
(II) RADEONHD(0): [drm] installed DRM signal handler
(II) RADEONHD(0): [pci] 16384 kB allocated with handle 0xf9688000
(II) RADEONHD(0): [pci] ring handle = 0xf9688000
(II) RADEONHD(0): [pci] Ring mapped at 0xa7092000
(II) RADEONHD(0): [pci] Ring contents 0x00000000
(II) RADEONHD(0): [pci] ring read ptr handle = 0xf9889000
(II) RADEONHD(0): [pci] Ring read ptr mapped at 0xa7091000
(II) RADEONHD(0): [pci] Ring read ptr contents 0x00000000
(II) RADEONHD(0): [pci] vertex/indirect buffers handle = 0xf988a000
(II) RADEONHD(0): [pci] Vertex/indirect buffers mapped at 0xa6e91000
(II) RADEONHD(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEONHD(0): [pci] GART texture map handle = 0xf9a8a000
(II) RADEONHD(0): [pci] GART Texture map mapped at 0xa62d1000
(II) RADEONHD(0): [drm] register handle = 0xfdfe0000
(II) RADEONHD(0): [dri] Visual configs initialized
(WW) RADEONHD(0): [drm] failed to enable new memory map
(II) RADEONHD(0): [drm] removed 1 reserved context for kernel
(II) RADEONHD(0): [drm] unmapping 8192 bytes of SAREA 0xf8229000 at 0xb7777000
(II) RADEONHD(0): [drm] Closed DRM master.
(II) RADEONHD(0): Attempting to set Engine Clock to 500000
(II) RADEONHD(0): Current Engine Clock: 501200
(WW) RADEONHD(0): AtomBIOS command table 47 does not exist
(II) RADEONHD(0): Query for AtomBIOS Exec: not implemented
(WW) RADEONHD(0): Unusupported SetVoltage Revision
(II) RADEONHD(0): Using MMIO Command Submission for acceleration.
(II) EXA(0): Offscreen pixmap area of 26841088 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) RADEONHD(0): Backing store disabled
(==) RADEONHD(0): Silken mouse enabled
(II) RADEONHD(0): Setting up "1280x720" (1280x720@60.0Hz)
None
(II) RADEONHD(0): Query for AtomBIOS Get Datatable from Codetable: failed
None
(II) RADEONHD(0): RHDAudioSetClock: using TMDS B as clock source with 74250 khz
(II) RADEONHD(0): Using ACR timing N=4096 CTS=74250 for frequency 32000
(II) RADEONHD(0): Using ACR timing N=6272 CTS=82500 for frequency 44100
(II) RADEONHD(0): Using ACR timing N=6144 CTS=74250 for frequency 48000
(II) RADEONHD(0): RHDAudioSetSupported: config 0x60040 codec 0x1
(II) RADEONHD(0): Using HW cursor
(==) RADEONHD(0): DPMS enabled
(II) RADEONHD(0): Xv: No Textured Video possible without the Command Processor.
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device G15 Gaming Keyboard (/dev/input/event4)
(**) G15 Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
(**) G15 Gaming Keyboard: always reports core events
(**) G15 Gaming Keyboard: Device: "/dev/input/event4"
(II) G15 Gaming Keyboard: Found keys
(II) G15 Gaming Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "G15 Gaming Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device G15 Gaming Keyboard (/dev/input/event5)
(**) G15 Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
(**) G15 Gaming Keyboard: always reports core events
(**) G15 Gaming Keyboard: Device: "/dev/input/event5"
(II) G15 Gaming Keyboard: Found keys
(II) G15 Gaming Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "G15 Gaming Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device G15 GamePanel LCD (/dev/input/event6)
(**) G15 GamePanel LCD: Applying InputClass "evdev keyboard catchall"
(**) G15 GamePanel LCD: always reports core events
(**) G15 GamePanel LCD: Device: "/dev/input/event6"
(II) G15 GamePanel LCD: Found keys
(II) G15 GamePanel LCD: Configuring as keyboard
(II) XINPUT: Adding extended input device "G15 GamePanel LCD" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Kensington Kensington USB/PS2 Orbit (/dev/input/event3)
(**) Kensington Kensington USB/PS2 Orbit: Applying InputClass "evdev pointer catchall"
(**) Kensington Kensington USB/PS2 Orbit: always reports core events
(**) Kensington Kensington USB/PS2 Orbit: Device: "/dev/input/event3"
(II) Kensington Kensington USB/PS2 Orbit: Found 3 mouse buttons
(II) Kensington Kensington USB/PS2 Orbit: Found relative axes
(II) Kensington Kensington USB/PS2 Orbit: Found x and y relative axes
(II) Kensington Kensington USB/PS2 Orbit: Configuring as mouse
(**) Kensington Kensington USB/PS2 Orbit: YAxisMapping: buttons 4 and 5
(**) Kensington Kensington USB/PS2 Orbit: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Kensington Kensington USB/PS2 Orbit" (type: MOUSE)
(II) Kensington Kensington USB/PS2 Orbit: initialized for relative axes.
(II) config/udev: Adding input device Kensington Kensington USB/PS2 Orbit (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: stopped with 2 channels, 44100 Hz sampling rate, 16 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x81 IEC60958 status bits and 0x02 category code
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: playing with 2 channels, 44100 Hz sampling rate, 16 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x81 IEC60958 status bits and 0x02 category code
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: stopped with 2 channels, 44100 Hz sampling rate, 16 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x81 IEC60958 status bits and 0x02 category code
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: playing with 2 channels, 44100 Hz sampling rate, 16 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x81 IEC60958 status bits and 0x02 category code
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: stopped with 2 channels, 44100 Hz sampling rate, 16 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x81 IEC60958 status bits and 0x02 category code
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) G15 Gaming Keyboard: Close
(II) UnloadModule: "evdev"
(II) G15 Gaming Keyboard: Close
(II) UnloadModule: "evdev"
(II) G15 GamePanel LCD: Close
(II) UnloadModule: "evdev"
(II) Kensington Kensington USB/PS2 Orbit: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) RADEONHD(0): Attempting to disable power management
(WW) RADEONHD(0): AtomBIOS command table 19 does not exist
(II) RADEONHD(0): Query for AtomBIOS Exec: not implemented
(WW) RADEONHD(0): Failed to set power management
(II) RADEONHD(0): Query for Set Power Management: failed
(II) RADEONHD(0): Attempting to disable clock gating
(II) RADEONHD(0): Attempting to set Engine Clock to 501200
(II) RADEONHD(0): Current Engine Clock: 501200
(WW) RADEONHD(0): AtomBIOS command table 47 does not exist
(II) RADEONHD(0): Query for AtomBIOS Exec: not implemented
(WW) RADEONHD(0): Unusupported SetVoltage Revision
 ddxSigGiveUp: Closing log
```So it seems to be a lack of support for my card. 

The easy way to setup the driver itself is.
1) Default install with radeon.
2) install the driver: open a terminal sudo apt-get install xserver-xorg-video-radeonhd
3) disable plymouth: 
sudo gedit /etc/default/grub
change "quiet splash" to

```
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
GRUB_CMDLINE_LINUX=""
```

save/close the file and update grub

sudo update-grub

4) make a record of display settings: sudo xrandr > xrandr-radeon.txt, so you have a record of what the display modes should look like with the default driver
5) change the driver: sudo gedit /usr/lib/X11/xorg.conf.d/device.conf

Add the following to device.conf

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver      "radeonhd"
        Option      "DRI" "on"
        Option      "AccelMethod" "EXA"
        Option      "NoRandr"
        Option      "HPD"  "Auto"
        Option      "Audio"  "true"
        Option      "HDMI"  "all"
EndSection


```Reboot.

6) login to a desktop and check the displays: sudo xrandr
*you could also test it with xrandr enabled just comment out the option in device.conf with #

**********To restore the original radeon driver just remove device.conf from the /usr/lib/X11/xorg.conf.d/ directory.**

That should work for most people. If you use more than 1 monitor at a time you'll probably have to do the modesetting yourself.

Full query of the options in the lucid radeonhd driver.

        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "offscreensize"          # [<str>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ignoreconnector"        # [<str>]
        #Option     "forcereduced"           # [<bool>]
        #Option     "forcedpi"               # <i>
        #Option     "useconfiguredmonitor"     # [<bool>]
        #Option     "HPD"                    # <str>
        #Option     "NoRandr"                # [<bool>]
        #Option     "RROutputOrder"          # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "TVMode"                 # [<str>]
        #Option     "ScaleType"              # [<str>]
        #Option     "UseAtomBIOS"            # [<bool>]
        #Option     "AtomBIOS"               # [<str>]
        #Option     "UnverifiedFeatures"     # [<bool>]
        #Option     "Audio"                  # [<bool>]
        #Option     "AudioStreamSilence"     # [<str>]
        #Option     "HDMI"                   # [<str>]
        #Option     "COHERENT"               # [<str>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "LowPowerModeEngineClock"     # <i>

Info regarding some of them.
[http://manpages.ubuntu.com/manpages/lucid/man4/radeonhd.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/radeonhd.4.html)

Anyway I guess I'm off to a hardy 8.04 ATI prop driver install since I can't expect updates to the radeonhd driver and even the 2.6.35 kernel with radeon doesn't support audio on my card. Man I hate ATI with linux. Nothing but headaches.

---

### Post by rick_ca on 2010-12-08
Did you ever get this figured out?

I'm having the same (or a similar) problem -- with an ATI Radeon Xpress 1200 series (RS600), but in Ubuntu 10.10.

Laptop audio works, and Ubuntu sees the device, but audio won't work over HDMI.

Frustrating.

---

### Post by tjones00 on 2010-12-12
Nope I tossed the system awhile ago. Back when I wrote this thread I understood very little about hdmi audio and alsa. I would revisit the issue for you but as I said I tossed the hardware.

If I were to take this on again I would stick with using the opensource "radeon" driver and work on troubleshooting alsa hdmi audio. The radeonhd hdmi audio is apparently being ported into the radeon driver. Unfortunately I only have experience with Nvidia hdmi audio so I can't tell you where to start with ATI hdmi audio using "radeon".

I did get hdmi audio working with the radeonhd driver but as stated 3d and advanced rendering didn't work (sucks for playing video). Atombios seems to be the issue with the old X1250 and radeonhd. I could never figure out how to aquire a proper one. 

If you follow the process I left here you should be able to successfully run the "radeonhd" driver. If you can get 3d and advanced rendering to work with your card setting up the hdmi audio is easy.

---

### Post by bubenkoff on 2011-02-01
Please help with a question: will ubuntu 10.10 work with ati x1300 with 2 monitors (one crt and second lcd, with different resolutions of course)
i need just video for crt and desktop on lcd, no need in audio through hdmi)

---

### Post by tjones00 on 2011-02-01
A lot of people seem to be having an issues with x1200-x1600 cards with 10.10. Unless you absolutely must upgrade to 10.10 I wouldn't go higher than 10.04 right now. 10.04 is the LTS release anyway.

My x1250 could handle two monitors just fine in 10.04 with the radeon/ati opensource driver.

---

### Post by bubenkoff on 2011-02-01
> **tjones00 said:**
> A lot of people seem to be having an issues with x1200-x1600 cards with 10.10. Unless you absolutely must upgrade to 10.10 I wouldn't go higher than 10.04 right now. 10.04 is the LTS release anyway.

My x1250 could handle two monitors just fine in 10.04 with the radeon/ati opensource driver.
upgrade is already done earlier, but card is not bought yet :)
thank you, will think about, may be better to get nvidia card instead

---

### Post by chuckd83 on 2011-07-28
I'm not sure if this has been solved, but I cannot get audio out through HDMI on my x1200. I am running 11.04. Has this been solved?

---


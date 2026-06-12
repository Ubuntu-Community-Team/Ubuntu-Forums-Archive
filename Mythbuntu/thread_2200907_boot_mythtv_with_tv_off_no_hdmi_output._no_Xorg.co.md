---
title: "boot mythtv with tv off no hdmi output. no Xorg.conf"
date: 2014-01-21
forum: Mythbuntu
---

### Post by ceesquared on 2014-01-21
This is reopening a closed thread with a twist.
Ubuntu 12.04, mythtv 0.25, combined BE/FE. MB (Intel) has onboard graphics. If Mythtv starts with the TV off (to do a recording) and I then switch on the tv, there is no HDMI output to the TV. A Google search talks about changing Xorg.conf BUT, I do not have an Xorg.conf. I do have an Xorg.0.log so something is generating the log. What do I change instead of Xorg.conf or alternatively, what do I restart after the tv goes on and how do I do it. If the answer is make your own Xorg.conf then please could I have an example.

---

### Post by blm-ubunet on 2014-01-23
As the xorg.conf file is not mandatory (any more), most people don't have one..
The intel driver should support HDMI hot-plugging.

The minimal file can be created by hand or from terminal:
```
sudo Xorg -configure
```

the basic file looks like this after some fiddling about:
```
# /etc/X11/xorg.conf
Section "Module"
#        Load          "dri"
#        Load          "glx"
EndSection

Section "DRI"
    Group "video"
    Mode 0660
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
#        Option          "AccelMethod" "EXA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

With a HDMI device switched off there is no EDID data to set output video mode so you have to force the output on & set a video mode..
DVI & VGA can read the EDID (DDC) with monitor off..

I have never bothered to force output with intel graphics..
The exact keywords to force the required output on for a nVidia card are:
# (in device section)
Option "ConnectedMonitor" "DFP1"
Option  "UseDisplayDevice"  "DFP1"
Intel driver uses different keywords & port names..so DFP1 could be TMDS-1 or HDMI-1 etc
The intel driver (& help) seems very incomplete compared to nVidia..

You should be able use xrandr (in some init script .xinit or .xprofile) to force the (HDMI) output on..but it has a hopeless help..
```
xrandr --addmode TMDS-1 1920x1080
xrandr --output TMDS-1 --mode 1920x1080
```
where 1920x1080 is a internal predefined modeline & TMDS-1 is your DVI or HDMI port

You could setup a keyboard button (multimedia) to launch a script that executes the above xrandr or just
xrandr --output TMDS-1 --auto

Failing all that there are kernel boot options..(as intel driver is KMS)..
[http://distro.ibiblio.org/fatdog/web/faqs/boot-options.html](http://distro.ibiblio.org/fatdog/web/faqs/boot-options.html)

Post your Xorg.0.log &/or output from "xrandr".

Intel driver updates:
Using intel graphics for mythtv can be underwhelming because the default intel driver etc (inc. VAAPI) in 12.04 is not up-to-date.

[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)
Great if you are using latest ubuntu..stable mythbuntu is 12.04LTS..14.04 will be ideal convergence.

Another alternative is xorg-edgers ppa
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise)
but this requires a backported kernel from later ubuntu raring.
(this will not update VAAPI packages)

both of these ppa could improve the HDMI hot-plugging events for video & audio..

---

### Post by ceesquared on 2014-01-24
Thank you blm-ubunet for your quick reply. I will have a go at your suggestions after the weekend.

---

### Post by ceesquared on 2014-01-28
Hi blm-ubunet, Thank you for your suggestions. I have had further investigations and narrowed down my options. For the benefit of other readers I will give my findings so far. If the TV ( a Panasonic ) is off/no power then the FE will not see the TV. There is no value in forcing HDMI as when the TV is switched on, the automatic input selection will not work as it uses a change of state to switch (no input to input). If the TV is switched on when the FE is outputting to HDMI then it does not see it as there is no change from off to on on the HDMI input. So the solution is to force HDMI output whilst the TV is on. So far so good. I have tried your suggestion of using xrandr and it partially works. I happen to use a shell which is called on the first press of a remote button and to this I have added:-

grep HDMI2 /var/log/Xorg.0.log | grep disconnected
if [ $? -eq 0 ] then;
   xrandr --output HDMI2 --auto
if

This works but only a quarter of the screen (top left ) is used. Display is 1920 x 1080. From the man for xrandr it gives examples of using a modeline, and this is where I need help and suggestions.

Here is my Xorg.0.log

[     9.508] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[     9.508] X Protocol Version 11, Revision 0
[     9.508] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[     9.508] Current Operating System: Linux MythTv 3.2.0-55-generic #85-Ubuntu SMP Wed Oct 2 12:29:27 UTC 2013 x86_64
[     9.508] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-55-generic root=UUID=a6c962f4-5f0e-4447-80c1-81a3fd3921f8 ro quiet splash vt.handoff=7
[     9.508] Build Date: 16 October 2013  04:41:23PM
[     9.508] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     9.508] Current version of pixman: 0.24.4
[     9.508]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     9.508] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.508] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 28 09:50:32 2014
[     9.508] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.521] (==) ServerLayout "X.org Configured"
[     9.521] (**) |-->Screen "Screen0" (0)
[     9.521] (**) |   |-->Monitor "Monitor0"
[     9.521] (**) |   |-->Device "Card0"
[     9.521] (==) Automatically adding devices
[     9.521] (==) Automatically enabling devices
[     9.521] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     9.521]     Entry deleted from font path.
[     9.521] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     9.521] (**) ModulePath set to "/usr/lib/xorg/modules"
[     9.521] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.521] (II) Loader magic: 0x7f56f2ffdb00
[     9.521] (II) Module ABI versions:
[     9.521]     X.Org ANSI C Emulation: 0.4
[     9.521]     X.Org Video Driver: 11.0
[     9.521]     X.Org XInput driver : 16.0
[     9.521]     X.Org Server Extension : 6.0
[     9.522] (--) PCI:*(0:0:2:0) 8086:0112:1043:844d rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[     9.522] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.522] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[     9.522] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[     9.522] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[     9.522] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[     9.522] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[     9.522] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[     9.522] (II) LoadModule: "record"
[     9.522] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.522] (II) Module record: vendor="X.Org Foundation"
[     9.522]     compiled for 1.11.3, module version = 1.13.0
[     9.522]     Module class: X.Org Server Extension
[     9.522]     ABI class: X.Org Server Extension, version 6.0
[     9.522] (II) Loading extension RECORD
[     9.522] (II) LoadModule: "dri"
[     9.523] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.523] (II) Module dri: vendor="X.Org Foundation"
[     9.523]     compiled for 1.11.3, module version = 1.0.0
[     9.523]     ABI class: X.Org Server Extension, version 6.0
[     9.523] (II) Loading extension XFree86-DRI
[     9.523] (II) LoadModule: "dbe"
[     9.523] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.523] (II) Module dbe: vendor="X.Org Foundation"
[     9.523]     compiled for 1.11.3, module version = 1.0.0
[     9.523]     Module class: X.Org Server Extension
[     9.523]     ABI class: X.Org Server Extension, version 6.0
[     9.523] (II) Loading extension DOUBLE-BUFFER
[     9.523] (II) LoadModule: "glx"
[     9.523] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     9.523] (II) Module glx: vendor="X.Org Foundation"
[     9.523]     compiled for 1.11.3, module version = 1.0.0
[     9.523]     ABI class: X.Org Server Extension, version 6.0
[     9.523] (==) AIGLX enabled
[     9.523] (II) Loading extension GLX
[     9.523] (II) LoadModule: "dri2"
[     9.523] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.523] (II) Module dri2: vendor="X.Org Foundation"
[     9.523]     compiled for 1.11.3, module version = 1.2.0
[     9.523]     ABI class: X.Org Server Extension, version 6.0
[     9.523] (II) Loading extension DRI2
[     9.523] (II) LoadModule: "extmod"
[     9.523] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.523] (II) Module extmod: vendor="X.Org Foundation"
[     9.523]     compiled for 1.11.3, module version = 1.0.0
[     9.523]     Module class: X.Org Server Extension
[     9.523]     ABI class: X.Org Server Extension, version 6.0
[     9.523] (II) Loading extension MIT-SCREEN-SAVER
[     9.523] (II) Loading extension XFree86-VidModeExtension
[     9.523] (II) Loading extension XFree86-DGA
[     9.523] (II) Loading extension DPMS
[     9.523] (II) Loading extension XVideo
[     9.523] (II) Loading extension XVideo-MotionCompensation
[     9.523] (II) Loading extension X-Resource
[     9.523] (II) LoadModule: "intel"
[     9.523] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     9.523] (II) Module intel: vendor="X.Org Foundation"
[     9.523]     compiled for 1.11.3, module version = 2.17.0
[     9.523]     Module class: X.Org Video Driver
[     9.523]     ABI class: X.Org Video Driver, version 11.0
[     9.523] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2)
[     9.524] (++) using VT number 7

[     9.525] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     9.525] drmOpenDevice: node name is /dev/dri/card0
[     9.525] drmOpenDevice: open result is 9, (OK)
[     9.525] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[     9.525] drmOpenDevice: node name is /dev/dri/card0
[     9.525] drmOpenDevice: open result is 9, (OK)
[     9.525] drmOpenByBusid: drmOpenMinor returns 9
[     9.525] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[     9.525] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     9.525] (==) intel(0): RGB weight 888
[     9.525] (==) intel(0): Default visual is TrueColor
[     9.525] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT2)
[     9.525] (--) intel(0): Chipset: "Sandybridge Desktop (GT2)"
[     9.525] (**) intel(0): Relaxed fencing enabled
[     9.525] (**) intel(0): Wait on SwapBuffers? enabled
[     9.525] (**) intel(0): Triple buffering? enabled
[     9.525] (**) intel(0): Framebuffer tiled
[     9.525] (**) intel(0): Pixmaps tiled
[     9.525] (**) intel(0): 3D buffers tiled
[     9.525] (**) intel(0): SwapBuffers wait enabled
[     9.525] (==) intel(0): video overlay key set to 0x101fe
[     9.525] (II) intel(0): Output VGA1 using monitor section Monitor0
[     9.532] (II) intel(0): Output HDMI1 has no monitor section
[     9.580] (II) intel(0): Output DP1 has no monitor section
[     9.897] (II) intel(0): Output HDMI2 has no monitor section
[     9.944] (II) intel(0): Output DP2 has no monitor section
[     9.944] (II) intel(0): EDID for output VGA1
[     9.948] (II) intel(0): EDID for output HDMI1
[     9.996] (II) intel(0): EDID for output DP1
[    10.250] (II) intel(0): EDID for output HDMI2
[    10.250] (II) intel(0): Manufacturer: MEI  Model: c135  Serial#: 16843009
[    10.250] (II) intel(0): Year: 2009  Week: 0
[    10.250] (II) intel(0): EDID Version: 1.3
[    10.250] (II) intel(0): Digital Display Input
[    10.250] (II) intel(0): Indeterminate output size
[    10.250] (II) intel(0): Gamma: 2.20
[    10.250] (II) intel(0): No DPMS capabilities specified
[    10.250] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    10.250] (II) intel(0): First detailed timing is preferred mode
[    10.250] (II) intel(0): redX: 0.640 redY: 0.345   greenX: 0.291 greenY: 0.635
[    10.250] (II) intel(0): blueX: 0.163 blueY: 0.093   whiteX: 0.288 whiteY: 0.296
[    10.250] (II) intel(0): Manufacturer's mask: 0
[    10.250] (II) intel(0): Supported detailed timing:
[    10.250] (II) intel(0): clock: 148.5 MHz   Image Size:  698 x 392 mm
[    10.250] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    10.250] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    10.250] (II) intel(0): Supported detailed timing:
[    10.250] (II) intel(0): clock: 148.5 MHz   Image Size:  698 x 392 mm
[    10.250] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    10.250] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    10.250] (II) intel(0): Monitor name: Panasonic-TV
[    10.250] (II) intel(0): Ranges: V min: 23 V max: 61 Hz, H min: 15 H max: 68 kHz, PixClock max 155 MHz
[    10.250] (II) intel(0): Supported detailed timing:
[    10.250] (II) intel(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    10.250] (II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    10.250] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    10.250] (II) intel(0): Supported detailed timing:
[    10.250] (II) intel(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    10.250] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    10.250] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    10.250] (II) intel(0): Supported detailed timing:
[    10.250] (II) intel(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    10.250] (II) intel(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    10.250] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    10.250] (II) intel(0): Supported detailed timing:
[    10.250] (II) intel(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    10.250] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    10.250] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    10.250] (II) intel(0): Supported detailed timing:
[    10.250] (II) intel(0): clock: 27.0 MHz   Image Size:  698 x 392 mm
[    10.250] (II) intel(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    10.250] (II) intel(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    10.250] (II) intel(0): Number of EDID sections to follow: 1
[    10.250] (II) intel(0): EDID (in hex):
[    10.250] (II) intel(0):     00ffffffffffff0034a935c101010101
[    10.250] (II) intel(0):     00130103800000780adaffa3584aa229
[    10.251] (II) intel(0):     17494b00000001010101010101010101
[    10.251] (II) intel(0):     010101010101023a80d072382d40102c
[    10.251] (II) intel(0):     4580ba882100001e023a801871382d40
[    10.251] (II) intel(0):     582c4500ba882100001e000000fc0050
[    10.251] (II) intel(0):     616e61736f6e69632d54560a000000fd
[    10.251] (II) intel(0):     00173d0f440f000a2020202020200122
[    10.251] (II) intel(0):     02032172509f90140520130412031102
[    10.251] (II) intel(0):     16071506012309070167030c001000b8
[    10.251] (II) intel(0):     26011d80d0721c1620102c2580ba8821
[    10.251] (II) intel(0):     00009e011d8018711c1620582c2500ba
[    10.251] (II) intel(0):     882100009e011d00bc52d01e20b82855
[    10.251] (II) intel(0):     40ba882100001e011d007251d01e206e
[    10.251] (II) intel(0):     285500ba882100001e8c0ad090204031
[    10.251] (II) intel(0):     200c405500ba8821000018000000001b
[    10.251] (II) intel(0): Printing probed modes for output HDMI2
[    10.251] (II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    10.251] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    10.296] (II) intel(0): EDID for output DP2
[    10.296] (II) intel(0): Output VGA1 disconnected
[    10.296] (II) intel(0): Output HDMI1 disconnected
[    10.296] (II) intel(0): Output DP1 disconnected
[    10.296] (II) intel(0): Output HDMI2 connected
[    10.296] (II) intel(0): Output DP2 disconnected
[    10.296] (II) intel(0): Using exact sizes for initial modes
[    10.296] (II) intel(0): Output HDMI2 using initial mode 1920x1080
[    10.296] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    10.296] (II) intel(0): Kernel page flipping support detected, enabling
[    10.296] (==) intel(0): DPI set to (96, 96)
[    10.296] (II) Loading sub module "fb"
[    10.296] (II) LoadModule: "fb"
[    10.296] (II) Loading /usr/lib/xorg/modules/libfb.so
[    10.296] (II) Module fb: vendor="X.Org Foundation"
[    10.296]     compiled for 1.11.3, module version = 1.0.0
[    10.296]     ABI class: X.Org ANSI C Emulation, version 0.4
[    10.296] (II) Loading sub module "dri2"
[    10.296] (II) LoadModule: "dri2"
[    10.296] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    10.296] (II) Module dri2: vendor="X.Org Foundation"
[    10.296]     compiled for 1.11.3, module version = 1.2.0
[    10.296]     ABI class: X.Org Server Extension, version 6.0
[    10.296] (==) Depth 24 pixmap format is 32 bpp
[    10.296] (II) intel(0): [DRI2] Setup complete
[    10.296] (II) intel(0): [DRI2]   DRI driver: i965
[    10.296] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[    10.297] (II) UXA(0): Driver registered support for the following operations:
[    10.297] (II)         solid
[    10.297] (II)         copy
[    10.297] (II)         composite (RENDER acceleration)
[    10.297] (II)         put_image
[    10.297] (II)         get_image
[    10.297] (==) intel(0): Backing store disabled
[    10.297] (==) intel(0): Silken mouse enabled
[    10.297] (II) intel(0): Initializing HW Cursor
[    10.356] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    10.356] (==) intel(0): DPMS enabled
[    10.356] (==) intel(0): Intel XvMC decoder enabled
[    10.356] (II) intel(0): Set up textured video
[    10.356] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    10.356] (II) intel(0): direct rendering: DRI2 Enabled
[    10.356] (==) intel(0): hotplug detection: "enabled"
[    10.356] (--) RandR disabled
[    10.356] (II) Initializing built-in extension Generic Event Extension
[    10.356] (II) Initializing built-in extension SHAPE
[    10.356] (II) Initializing built-in extension MIT-SHM
[    10.356] (II) Initializing built-in extension XInputExtension
[    10.356] (II) Initializing built-in extension XTEST
[    10.356] (II) Initializing built-in extension BIG-REQUESTS
[    10.356] (II) Initializing built-in extension SYNC
[    10.356] (II) Initializing built-in extension XKEYBOARD
[    10.356] (II) Initializing built-in extension XC-MISC
[    10.356] (II) Initializing built-in extension SECURITY
[    10.356] (II) Initializing built-in extension XINERAMA
[    10.356] (II) Initializing built-in extension XFIXES
[    10.356] (II) Initializing built-in extension RENDER
[    10.356] (II) Initializing built-in extension RANDR
[    10.356] (II) Initializing built-in extension COMPOSITE
[    10.356] (II) Initializing built-in extension DAMAGE
[    10.361] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    10.361] (II) AIGLX: enabled GLX_INTEL_swap_event
[    10.361] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    10.361] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    10.361] (II) AIGLX: Loaded and initialized i965
[    10.361] (II) GLX: Initialized DRI2 GL provider for screen 0
[    10.361] (II) intel(0): Setting screen physical size to 508 x 285
[    10.367] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.369] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    10.369] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.369] (II) LoadModule: "evdev"
[    10.369] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.369] (II) Module evdev: vendor="X.Org Foundation"
[    10.369]     compiled for 1.11.3, module version = 2.7.0
[    10.369]     Module class: X.Org XInput Driver
[    10.369]     ABI class: X.Org XInput driver, version 16.0
[    10.369] (II) Using input driver 'evdev' for 'Power Button'
[    10.369] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.369] (**) Power Button: always reports core events
[    10.369] (**) evdev: Power Button: Device: "/dev/input/event1"
[    10.369] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.369] (--) evdev: Power Button: Found keys
[    10.369] (II) evdev: Power Button: Configuring as keyboard
[    10.369] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    10.369] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    10.369] (**) Option "xkb_rules" "evdev"
[    10.369] (**) Option "xkb_model" "pc105"
[    10.369] (**) Option "xkb_layout" "gb"
[    10.370] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    10.371] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    10.371] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    10.371] (II) Using input driver 'evdev' for 'Video Bus'
[    10.371] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.371] (**) Video Bus: always reports core events
[    10.371] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    10.371] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    10.371] (--) evdev: Video Bus: Found keys
[    10.371] (II) evdev: Video Bus: Configuring as keyboard
[    10.371] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7/event7"
[    10.371] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    10.371] (**) Option "xkb_rules" "evdev"
[    10.371] (**) Option "xkb_model" "pc105"
[    10.371] (**) Option "xkb_layout" "gb"
[    10.371] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    10.371] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.371] (II) Using input driver 'evdev' for 'Power Button'
[    10.371] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.371] (**) Power Button: always reports core events
[    10.371] (**) evdev: Power Button: Device: "/dev/input/event0"
[    10.371] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.371] (--) evdev: Power Button: Found keys
[    10.371] (II) evdev: Power Button: Configuring as keyboard
[    10.371] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    10.371] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    10.371] (**) Option "xkb_rules" "evdev"
[    10.371] (**) Option "xkb_model" "pc105"
[    10.371] (**) Option "xkb_layout" "gb"
[    10.372] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event10)
[    10.372] (II) No input driver specified, ignoring this device.
[    10.372] (II) This device may have been added with another device file.
[    10.372] (II) config/udev: Adding input device HDA Intel PCH Line-Out (/dev/input/event11)
[    10.372] (II) No input driver specified, ignoring this device.
[    10.372] (II) This device may have been added with another device file.
[    10.372] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event8)
[    10.372] (II) No input driver specified, ignoring this device.
[    10.372] (II) This device may have been added with another device file.
[    10.372] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event9)
[    10.372] (II) No input driver specified, ignoring this device.
[    10.372] (II) This device may have been added with another device file.
[    10.372] (II) config/udev: Adding input device Darfon USB Optical Mouse (/dev/input/event3)
[    10.372] (**) Darfon USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    10.372] (II) Using input driver 'evdev' for 'Darfon USB Optical Mouse'
[    10.372] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.372] (**) Darfon USB Optical Mouse: always reports core events
[    10.372] (**) evdev: Darfon USB Optical Mouse: Device: "/dev/input/event3"
[    10.372] (--) evdev: Darfon USB Optical Mouse: Vendor 0xd62 Product 0xa100
[    10.372] (--) evdev: Darfon USB Optical Mouse: Found 3 mouse buttons
[    10.372] (--) evdev: Darfon USB Optical Mouse: Found scroll wheel(s)
[    10.372] (--) evdev: Darfon USB Optical Mouse: Found relative axes
[    10.372] (--) evdev: Darfon USB Optical Mouse: Found x and y relative axes
[    10.372] (II) evdev: Darfon USB Optical Mouse: Configuring as mouse
[    10.372] (II) evdev: Darfon USB Optical Mouse: Adding scrollwheel support
[    10.372] (**) evdev: Darfon USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    10.372] (**) evdev: Darfon USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.372] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/usb3/3-2/3-2:1.0/input/input3/event3"
[    10.372] (II) XINPUT: Adding extended input device "Darfon USB Optical Mouse" (type: MOUSE, id 9)
[    10.372] (II) evdev: Darfon USB Optical Mouse: initialized for relative axes.
[    10.372] (**) Darfon USB Optical Mouse: (accel) keeping acceleration scheme 1
[    10.372] (**) Darfon USB Optical Mouse: (accel) acceleration profile 0
[    10.372] (**) Darfon USB Optical Mouse: (accel) acceleration factor: 2.000
[    10.372] (**) Darfon USB Optical Mouse: (accel) acceleration threshold: 4
[    10.373] (II) config/udev: Adding input device Darfon USB Optical Mouse (/dev/input/mouse0)
[    10.373] (II) No input driver specified, ignoring this device.
[    10.373] (II) This device may have been added with another device file.
[    10.373] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event4)
[    10.373] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    10.373] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[    10.373] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.373] (**) Eee PC WMI hotkeys: always reports core events
[    10.373] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event4"
[    10.373] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[    10.373] (--) evdev: Eee PC WMI hotkeys: Found keys
[    10.373] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[    10.373] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input4/event4"
[    10.373] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 10)
[    10.373] (**) Option "xkb_rules" "evdev"
[    10.373] (**) Option "xkb_model" "pc105"
[    10.373] (**) Option "xkb_layout" "gb"
[    10.373] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    10.373] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    10.373] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    10.373] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.373] (**) AT Translated Set 2 keyboard: always reports core events
[    10.373] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    10.373] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    10.373] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    10.373] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    10.373] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    10.373] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    10.373] (**) Option "xkb_rules" "evdev"
[    10.373] (**) Option "xkb_model" "pc105"
[    10.373] (**) Option "xkb_layout" "gb"
[    10.374] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (saa716x) (/dev/input/event6)
[    10.374] (**) MCE IR Keyboard/Mouse (saa716x): Applying InputClass "evdev pointer catchall"
[    10.374] (**) MCE IR Keyboard/Mouse (saa716x): Applying InputClass "evdev keyboard catchall"
[    10.374] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (saa716x)'
[    10.374] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.374] (**) MCE IR Keyboard/Mouse (saa716x): always reports core events
[    10.374] (**) evdev: MCE IR Keyboard/Mouse (saa716x): Device: "/dev/input/event6"
[    10.374] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Vendor 0 Product 0
[    10.374] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Found 3 mouse buttons
[    10.374] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Found relative axes
[    10.374] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Found x and y relative axes
[    10.374] (--) evdev: MCE IR Keyboard/Mouse (saa716x): Found keys
[    10.374] (II) evdev: MCE IR Keyboard/Mouse (saa716x): Configuring as mouse
[    10.374] (II) evdev: MCE IR Keyboard/Mouse (saa716x): Configuring as keyboard
[    10.374] (**) evdev: MCE IR Keyboard/Mouse (saa716x): YAxisMapping: buttons 4 and 5
[    10.374] (**) evdev: MCE IR Keyboard/Mouse (saa716x): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.374] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    10.374] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (saa716x)" (type: KEYBOARD, id 12)
[    10.374] (**) Option "xkb_rules" "evdev"
[    10.374] (**) Option "xkb_model" "pc105"
[    10.375] (**) Option "xkb_layout" "gb"
[    10.375] (II) evdev: MCE IR Keyboard/Mouse (saa716x): initialized for relative axes.
[    10.375] (**) MCE IR Keyboard/Mouse (saa716x): (accel) keeping acceleration scheme 1
[    10.375] (**) MCE IR Keyboard/Mouse (saa716x): (accel) acceleration profile 0
[    10.375] (**) MCE IR Keyboard/Mouse (saa716x): (accel) acceleration factor: 2.000
[    10.375] (**) MCE IR Keyboard/Mouse (saa716x): (accel) acceleration threshold: 4
[    10.375] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (saa716x) (/dev/input/mouse1)
[    10.375] (II) No input driver specified, ignoring this device.
[    10.375] (II) This device may have been added with another device file.
[    11.211] (II) intel(0): EDID vendor "MEI", prod id 49461
[    11.211] (II) intel(0): Using EDID range info for horizontal sync
[    11.211] (II) intel(0): Using EDID range info for vertical refresh
[    11.211] (II) intel(0): Printing DDC gathered Modelines:
[    11.211] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    11.211] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    11.211] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    11.211] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    11.211] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    11.211] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    11.211] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    11.211] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    11.211] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    11.211] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    11.211] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    11.211] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    11.211] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    11.211] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    11.631] (II) intel(0): EDID vendor "MEI", prod id 49461
[    11.631] (II) intel(0): Using hsync ranges from config file
[    11.631] (II) intel(0): Using vrefresh ranges from config file
[    11.631] (II) intel(0): Printing DDC gathered Modelines:
[    11.631] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    11.631] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    11.631] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    11.631] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    11.631] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    11.631] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    11.631] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    11.631] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    11.631] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    11.631] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    11.631] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    11.631] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    11.631] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    11.631] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    11.990] (II) config/udev: Adding input device saa716x IR (TurboSight TBS 6984) (/dev/input/event5)
[    11.990] (**) saa716x IR (TurboSight TBS 6984): Applying InputClass "evdev keyboard catchall"
[    11.990] (II) Using input driver 'evdev' for 'saa716x IR (TurboSight TBS 6984)'
[    11.990] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.990] (**) saa716x IR (TurboSight TBS 6984): always reports core events
[    11.990] (**) evdev: saa716x IR (TurboSight TBS 6984): Device: "/dev/input/event5"
[    11.990] (--) evdev: saa716x IR (TurboSight TBS 6984): Vendor 0x6984 Product 0x13
[    11.990] (--) evdev: saa716x IR (TurboSight TBS 6984): Found keys
[    11.990] (II) evdev: saa716x IR (TurboSight TBS 6984): Configuring as keyboard
[    11.990] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/rc/rc0/input5/event5"
[    11.990] (II) XINPUT: Adding extended input device "saa716x IR (TurboSight TBS 6984)" (type: KEYBOARD, id 13)
[    11.990] (**) Option "xkb_rules" "evdev"
[    11.990] (**) Option "xkb_model" "pc105"
[    11.990] (**) Option "xkb_layout" "gb"
[    12.567] (II) intel(0): EDID vendor "MEI", prod id 49461
[    12.567] (II) intel(0): Using hsync ranges from config file
[    12.567] (II) intel(0): Using vrefresh ranges from config file
[    12.567] (II) intel(0): Printing DDC gathered Modelines:
[    12.567] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    12.567] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    12.567] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    12.567] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    12.567] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    12.567] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    12.567] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    12.567] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    12.567] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    12.567] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    12.567] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    12.567] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    12.567] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    12.567] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    12.903] (II) intel(0): EDID vendor "MEI", prod id 49461
[    12.903] (II) intel(0): Using hsync ranges from config file
[    12.903] (II) intel(0): Using vrefresh ranges from config file
[    12.903] (II) intel(0): Printing DDC gathered Modelines:
[    12.903] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    12.903] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    12.903] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    12.903] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    12.903] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    12.903] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    12.903] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    12.903] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    12.903] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    12.903] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    12.903] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    12.903] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    12.903] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    12.903] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    13.242] (II) intel(0): EDID vendor "MEI", prod id 49461
[    13.242] (II) intel(0): Using hsync ranges from config file
[    13.242] (II) intel(0): Using vrefresh ranges from config file
[    13.242] (II) intel(0): Printing DDC gathered Modelines:
[    13.242] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    13.242] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    13.242] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    13.242] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    13.242] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    13.242] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    13.242] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    13.242] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    13.242] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    13.242] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    13.242] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    13.242] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    13.242] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    13.242] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    20.415] (II) intel(0): EDID vendor "MEI", prod id 49461
[    20.415] (II) intel(0): Using hsync ranges from config file
[    20.415] (II) intel(0): Using vrefresh ranges from config file
[    20.415] (II) intel(0): Printing DDC gathered Modelines:
[    20.415] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    20.415] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    20.415] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    20.415] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    20.415] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    20.415] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    20.415] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    20.415] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    20.415] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    20.415] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    20.415] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    20.415] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    20.415] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    20.415] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    20.747] (II) intel(0): EDID vendor "MEI", prod id 49461
[    20.747] (II) intel(0): Using hsync ranges from config file
[    20.747] (II) intel(0): Using vrefresh ranges from config file
[    20.747] (II) intel(0): Printing DDC gathered Modelines:
[    20.747] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    20.747] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    20.747] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[    20.747] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    20.747] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    20.747] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    20.747] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    20.747] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[    20.747] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[    20.747] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    20.747] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[    20.747] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    20.747] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[    20.747] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[   197.122] (II) intel(0): EDID vendor "MEI", prod id 49461
[   197.122] (II) intel(0): Using hsync ranges from config file
[   197.122] (II) intel(0): Using vrefresh ranges from config file
[   197.122] (II) intel(0): Printing DDC gathered Modelines:
[   197.122] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[   197.122] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   197.122] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz)
[   197.122] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[   197.122] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[   197.122] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[   197.122] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[   197.122] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz)
[   197.122] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz)
[   197.122] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[   197.123] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[   197.123] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[   197.123] (II) intel(0): Modeline "1440x288"x0.0   27.00  1440 1464 1590 1728  288 290 293 312 -hsync -vsync (15.6 kHz)
[   197.123] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)

And my output of xrandr --verbose

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x41
    Timestamp:  9508
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
HDMI1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x42
    Timestamp:  9508
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    Broadcast RGB:    Full
        supported: Full         Limited 16:2
    audio:    auto
        supported: off          auto         on          
DP1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x43
    Timestamp:  9508
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    Broadcast RGB:    Full
        supported: Full         Limited 16:2
    audio:    auto
        supported: off          auto         on          
HDMI2 connected 1920x1080+0+0 (0x46) normal (normal left inverted right x axis y axis) 698mm x 392mm
    Identifier: 0x44
    Timestamp:  9508
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff0034a935c101010101
        00130103800000780adaffa3584aa229
        17494b00000001010101010101010101
        010101010101023a80d072382d40102c
        4580ba882100001e023a801871382d40
        582c4500ba882100001e000000fc0050
        616e61736f6e69632d54560a000000fd
        00173d0f440f000a2020202020200122
        02032172509f90140520130412031102
        16071506012309070167030c001000b8
        26011d80d0721c1620102c2580ba8821
        00009e011d8018711c1620582c2500ba
        882100009e011d00bc52d01e20b82855
        40ba882100001e011d007251d01e206e
        285500ba882100001e8c0ad090204031
        200c405500ba8821000018000000001b
    Broadcast RGB:    Full
        supported: Full         Limited 16:2
    audio:    auto
        supported: off          auto         on          
  1920x1080 (0x46)  148.5MHz +HSync +VSync *current +preferred
        h: width  1920 start 2448 end 2492 total 2640 skew    0 clock   56.2KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   50.0Hz
  1920x1080 (0x47)  148.5MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   60.0Hz
DP2 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x45
    Timestamp:  9508
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    Broadcast RGB:    Full
        supported: Full         Limited 16:2
    audio:    auto
        supported: off          auto         on

Sorry about filling up the page but I don't know how to put it in a window!

---

### Post by blm-ubunet on 2014-02-01
The hot-plug event is reporting EDID & likely the ELD (audio)..
Your HDIM2 display reported modeline is fine...
> [    10.251] (II) intel(0): Printing probed modes for output HDMI2
[    10.251] (II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
[    10.251] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)

the 60Hz mode timing is reduced blanking (good).

Could try:
```
xrandr --addmode HDMI2 1920x1080
xrandr --output HDMI2 --mode 1920x1080
```
or maybe to force display to use all
```
xrandr --output HDMI2 --size 1920x1080
```

If you need to switch between 50Hz & 60Hz modes then you have to specify the mode name more explicitly..
Need to see output from:
xrandr

---

### Post by ceesquared on 2014-02-03
Thanks blm-ubunet. I was half way there with your hint at looking at the log and xrandr output. for the benefit of future readers my solution was to add to a script that is called on the first button press of the remote

grep HDMI2 /var/log/Xorg.0.log | grep disconnected > /dev/null
# if HDMI2 ( the TV ) disconnected
if [ $? -eq 0 ]; then
# generate a new mode extracted from xrandr --verbose , The line that says *current +preferred
   xrandr --newmode "panhdmi" 148.5 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
   xrandr --addmode HDMI2 panhdmi
   xrandr --output HDMI2 --mode panhdmi
fi

Now how do I close this thread as answered?

---

### Post by blm-ubunet on 2014-02-03
Good that it works.

I don't think you need to generate a modeline with a new name..for 2 reasons..

- X server (very likely) has built-in 1920x1080 RVT mode
- your monitor reports valid 1920x1080 mode..

Problem is to "get" the name of the modeline..xrandr is not very helpful here..
Normally you would only create a new modeline (--newmode)  if there is no internal or EDID modes available.

---

### Post by johalareewi on 2014-02-06
I could have a similar problem with my BE/FE unit (ATI Radeon graphics).  Connection to TV is via HDMI.  Sometimes get black screen when switching TV to the Myth HDMI input.  Wasn't sure how, but it could be where the PC was rebooted with the TV off.

---

### Post by ceesquared on 2014-02-07
The glitch here is booting up with TV off(i.e. no TV power). As far as Myth is concerned, no TV is connected (TV off) and so it cannot collect EDID modes. I havn't a clue on what the name is of the internal mode so the answer is to boot with TV on, use xrander to find out what EDID it collected and then reproduce this as a newmode and use a script to force it. If you want to Know how to do a first remote press action I detailed it on the discussion page of the Mythtv wiki on ACPI.

---


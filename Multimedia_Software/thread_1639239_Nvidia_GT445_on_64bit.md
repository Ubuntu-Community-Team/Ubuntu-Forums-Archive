---
title: "Nvidia GT445 on 64bit"
date: 2010-12-06
forum: Multimedia Software
---

### Post by arpoodle on 2010-12-06
This is an extension of the post I put in the Dell forum, but it's probbaly more relevant here, as it's not specifically a Dell issue any more.

I've got a Dell XPS 17 onto which I've installed Ubuntu 10.4, 64bit.

The standard install doesn't recognise the video card, and defaults to a 800x600 output.

Nvidia don't list a 64bit driver for the GT445 for Linux, however the GT435 driver seems to work.

That being said, I've now installed the laptop at my desk, and plugged the second display into the HDMI port on the laptop.
On the old laptop, an Inspiron, the Nvidia display manager app would  detect the display and give a "twin view" option to spread the desktop  across both displays.

The display manager app on the new install doesn't detect the second  display, and xrandr suggests it's unaware that it's there at all.
I've even manually added the "twin-view" setting to the xorg.conf file,  but obviously without it knowing there's a second display present,  that's not going to do much.

Does anyone know if Nvidia have plans for a 64bit Linux driver for the GT445?
Does the GT435 support HDMI? and if so, then why does the native display work and the external HDMI doesn't?

Any hints to get this second display working?

xrandr and other relevant outputs below:

> 
root@hiro:~# uname -a
Linux hiro 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux
root@hiro:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid
root@hiro:~# xrandr
Screen 0: minimum 320 x 175, current 1600 x 900, maximum 1600 x 900
default connected 1600x900+0+0 0mm x 0mm
   1600x900       50.0* 
   1360x768       51.0     52.0  
   1152x864       53.0  
   1024x768       54.0     55.0     56.0     57.0     58.0  
   960x600        59.0  
   960x540        60.0  
   840x525        61.0     62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0     72.0     73.0  
   800x512        74.0  
   720x450        75.0  
   720x400        76.0  
   700x525        77.0     78.0     79.0     80.0  
   680x384        81.0     82.0  
   640x512        83.0     84.0     85.0  
   640x480        86.0     87.0     88.0     89.0     90.0     91.0  
   640x400        92.0  
   640x350        93.0  
   576x432        94.0     95.0     96.0     97.0     98.0     99.0    100.0  
   512x384       101.0    102.0    103.0    104.0    105.0  
   416x312       106.0  
   400x300       107.0    108.0    109.0    110.0    111.0  
   360x200       112.0  
   320x240       113.0    114.0    115.0    116.0  
   320x200       117.0  
   320x175       118.0



---

### Post by inobe on 2010-12-06
you need the 445m for notebooks

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

edit: stupid link.

in the drop down choose 400m, the next drop down below select 445m and finally linux 64bit.

i believe they are beta's.

---

### Post by arpoodle on 2010-12-06
> **inobe said:**
> you need the 445m for notebooks

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

edit: stupid link.

in the drop down choose 400m, the next drop down below select 445m and finally linux 64bit.

i believe they are beta's.
Yes, I've done that already:

" 								**No results.**"

Which is how I ended up trying the 435 driver.

There was no link to any Beta drivers there

---

### Post by arpoodle on 2010-12-07
after a hard reboot, the second display is showing up in the settings tool.

I can also select it as twin-view as I want.

However, the display is just sitting in sleep/power-saving mode and isn't receiving a signal.

Also, in the xorg.conf, I can't see any reference to the second display.

> Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko/Epson"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 445M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1600+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


In /var/log/Xorg.0.log, the only entries I can see when changing the twinview settings and adding the second display are:

> (II) Dec 07 09:41:14 NVIDIA(0): Setting mode
(II) Dec 07 09:41:14 NVIDIA(0):     "DFP-0:nvidia-auto-select@1600x900+0+0,DFP-1:nvidia-auto-select@1920x1080+1600+0"

---

### Post by arpoodle on 2010-12-07
I manually added the second display to xorg.conf and now it works.

It would seem that the nvidia settings tool wasn't writing out all the settings properly

---

### Post by psnel on 2011-01-28
Just to summarize:
- You got the GT445 to work using the GT435 64-bit driver from NVIDIA
- You got the both the primary display and external hdmi display to work

Questions:
1) Did you ever get the better resolution (1600x900) on your primary display?
2) Which driver version? Have you tried the latest release? (21 Jan, 2011 - still no 445GT)
3) Ubuntu 10.10 64bit?
4) What cpu? (e.g i5 has integrated gfx that can cause 'hybrid-switching' problems, i7-quad has none)

Sorry for all the q's. I don't have one, so can't test myself. Considering buying one.

---

### Post by arpoodle on 2011-01-28
> **psnel said:**
> Just to summarize:
- You got the GT445 to work using the GT435 64-bit driver from NVIDIA
- You got the both the primary display and external hdmi display to work

Questions:
1) Did you ever get the better resolution (1600x900) on your primary display?
2) Which driver version? Have you tried the latest release? (21 Jan, 2011 - still no 445GT)
3) Ubuntu 10.10 64bit?
4) What cpu? (e.g i5 has integrated gfx that can cause 'hybrid-switching' problems, i7-quad has none)

Sorry for all the q's. I don't have one, so can't test myself. Considering buying one.

Using the i7 CPU.

I got the primary display operating at 1600*900, yes.

Now, it was all working fine until a couple of weeks ago. Full resolution, full colour.  Then I'm not sure what it was, but after a regular ubuntu upgrade, the secondary screen dropped it's colour depth from 24 to 16. The Primary display is still operating at full colour depth.  The resolutions were unaffected.

I installed the latest Nvidia driver, but I'm still suffering the same thing.

I can work with it, as most of my work is done on the command line, but it's annoying me that the secondary screen, which is the larger of the two and the one I use most, is now looking like something from the 80's

---

### Post by psnel on 2011-01-28
Good enough for me :)
(Thanks for the quick reply, btw)

I'm a developer myself, mostly using multiple desktops in main display for heavy multitasking (db, appserver, compilers, skype, multiple browsers, shells, docs, etc) - but I watch alot of movies etc. too - hoped the HDMI would plug nicely into my home-theatre, but no biggy.

Hoping the screen quality problems ('light bleed through') won't be too much of a pain (esp. with my preference for dark themes). What's your experience?

As things stand, i'm ordering one tomorrow morning.

---

### Post by arpoodle on 2011-01-28
Generally, I'm very happy with it. Really can't complain. I don't think you'll be disappointed.

---

### Post by tessien on 2011-01-28
Hi arpoodle, I'm considering this laptop as well and I'm mainly worried about suspend-to-RAM, especially with the graphics card not being officialy supported. Any chance you have tried suspend-to-RAM or hibernate?

---

### Post by psnel on 2011-01-29
Supplier's closed, so can only order Monday morning. Tough luck.
Give's me time to benefit from further answers in this thread.

For the record, we're talking about the Dell XPS 17 ...
Specs *(the one I'm looking at)*:

**[COLOR="red"]DELL XPS 17[/COLOR] L701x**, 17.3 inch HD+WLED (1600 x 900), Intel Core i7-740QM (1.73GHz), 6GB (1x2GB and 1X4Gb) 1333MHz DDR3, 640GB (7200RPM), 8X DVD+-RW, MS WIN 7 PRO (64BIT) - boo!, 802.11 (n) and BLUETOOTH, **NVIDIA GeForce gt [COLOR="Red"]445M[/COLOR] 3GB**, 9-cell 90WHr Li-Ion Battery

---

### Post by arpoodle on 2011-01-29
> **tessien said:**
> Hi arpoodle, I'm considering this laptop as well and I'm mainly worried about suspend-to-RAM, especially with the graphics card not being officialy supported. Any chance you have tried suspend-to-RAM or hibernate?


Haven't tried that. I use my laptop more as a mobile desktop, so it's either on or off.

If I find 5 minutes I'll try it later today.

a

---

### Post by Jackobyt on 2011-01-29
> **tessien said:**
> Hi arpoodle, I'm considering this laptop as well and I'm mainly worried about suspend-to-RAM, especially with the graphics card not being officialy supported. Any chance you have tried suspend-to-RAM or hibernate?
I have the same system more or less (L701x with i7 740QM, 3gb 445M graphics, 4gb RAM, 500gb HDD, CD/DVD RW and BD ROM disc drive, 9 cell battery) and I am really happy with it. I've Win 7(64 bit), Ubuntu 10.10 (32 bit) and Peppermint One(32 bit). I could have installed Ubuntu 64bit, but it was my first venture into linux and I wasn't sure what I was doing. I haven't suspended to RAM yet but I'll try it now and get back to you.

Also, in regards to drivers for the graphics card, there is no problem with the 32 bit ones.

EDIT; Couldn't return from Suspend. Didn't try hibernate.

---

### Post by tessien on 2011-01-30
Thanks a lot guys, looks like I will have to live without suspend, at least until nVidia supports the card officially...

---

### Post by eXt on 2011-02-01
> **arpoodle said:**
> I manually added the second display to xorg.conf and now it works.

It would seem that the nvidia settings tool wasn't writing out all the settings properly

Hey! I've got the same problem :/ Would you like to share your xorg.conf? I can't get my second monitor to work :/

---

### Post by psnel on 2011-02-01
> **psnel said:**
> Supplier's closed, so can only order Monday morning. Tough luck.
Give's me time to benefit from further answers in this thread.

For the record, we're talking about the Dell XPS 17 ...
Specs *(the one I'm looking at)*:

**[COLOR="red"]DELL XPS 17[/COLOR] L701x**, 17.3 inch HD+WLED (1600 x 900), Intel Core i7-740QM (1.73GHz), 6GB (1x2GB and 1X4Gb) 1333MHz DDR3, 640GB (7200RPM), 8X DVD+-RW, MS WIN 7 PRO (64BIT) - boo!, 802.11 (n) and BLUETOOTH, **NVIDIA GeForce gt [COLOR="Red"]445M[/COLOR] 3GB**, 9-cell 90WHr Li-Ion Battery

Just setup Ubuntu 10.10 64 bit. Had some installation problems, but that seemed to have been due to a bad .iso (repeated DL, again. mirror DL worked on USB install)

Very pleasantly surprized! Everything so far works. Haven't tried to hibernate or anything much else, but the nvidea restricted driver is picked up automatically ->System->Administration->Additional Drivers

Installed all Update manager's updates, rebooted, resolution @ 1600x900; Nvidea's X server settings aps reports Nvidea Driver version: 260.19.06 - i'll try the newer one later, but don't want to push my luck just yet :)

Didn't have to do anything special.

Man! This is cool.

I'll report back with more experience - but that might be venturing off the topic...

---

### Post by arpoodle on 2011-02-03
> **eXt said:**
> Hey! I've got the same problem :/ Would you like to share your xorg.conf? I can't get my second monitor to work :/

xorg.conf as follows:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.36  (buildmeister@swio-display-x86-rhel47-01.nvidia.com)  Tue Jan 18 17:15:10 PST 2011

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.36  (buildmeister@swio-display-x86-rhel47-01.nvidia.com)  Tue Jan 18 17:15:22 PST 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko/Epson"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 445M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1600+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

I've noticed that I'm getting a lot of errors in the Xorg.0.log file relating to my second display.  Can anyone identify if they are related to the colour depth issue on display2? (not all the log file is included for brevity)

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux hiro 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-28-generic root=UUID=40440c89-e8d8-4ec4-8da1-5ec95561567b ro quiet splash
Build Date: 10 December 2010  05:52:57PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb  3 19:12:35 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 6.0
        X.Org XInput driver : 7.0
        X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:2:0:0) 10de:0dd2:1028:046c nVidia Corporation rev 161, Mem @ 0xc8000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x00002000/128, BIOS @ 0x????????/524288
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
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
(II) NVIDIA GLX Module  260.19.36  Tue Jan 18 17:12:12 PST 2011
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  260.19.36  Tue Jan 18 16:57:32 PST 2011
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1600+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-1"
(**) Feb 03 19:12:35 NVIDIA(0): Enabling RENDER acceleration
(II) Feb 03 19:12:35 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Feb 03 19:12:35 NVIDIA(0):     enabled.
(II) Feb 03 19:12:37 NVIDIA(0): NVIDIA GPU GeForce GT 445M (GF106) at PCI:2:0:0 (GPU-0)
(--) Feb 03 19:12:37 NVIDIA(0): Memory: 3145728 kBytes
(--) Feb 03 19:12:37 NVIDIA(0): VideoBIOS: 70.06.0e.00.03
(II) Feb 03 19:12:37 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Feb 03 19:12:37 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Feb 03 19:12:37 NVIDIA(0): Connected display device(s) on GeForce GT 445M at PCI:2:0:0
(--) Feb 03 19:12:37 NVIDIA(0):     Seiko/Epson (DFP-0)
(--) Feb 03 19:12:37 NVIDIA(0):     LG Electronics W2361 (DFP-1)
(--) Feb 03 19:12:37 NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
(--) Feb 03 19:12:37 NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
(--) Feb 03 19:12:37 NVIDIA(0): LG Electronics W2361 (DFP-1): 165.0 MHz maximum pixel clock
(--) Feb 03 19:12:37 NVIDIA(0): LG Electronics W2361 (DFP-1): Internal Single Link TMDS
(**) Feb 03 19:12:37 NVIDIA(0): TwinView enabled
(II) Feb 03 19:12:37 NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid HorizSync range (30.000-83.000 kHz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's HorizSync (28.1 kHz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     HorizSync check for mode "1920x1080".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1920x1080".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "720x576".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1920x1080".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1280x720" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1280x720".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1280x1024" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (75.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1280x1024".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1152x864" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (75.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1152x864".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "640x480" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (75.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "640x480".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "800x600" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (75.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "800x600".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1024x768" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (75.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1024x768".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid HorizSync range (30.000-83.000 kHz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's HorizSync (28.1 kHz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     HorizSync check for mode "1920x1080".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1920x1080".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "720x576".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1920x1080".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1280x720" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1280x720".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1280x1024" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (75.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1280x1024".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1152x864" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (75.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1152x864".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "640x480" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (75.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "640x480".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "800x600" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (75.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "800x600".
(WW) Feb 03 19:12:37 NVIDIA(0): The EDID for LG Electronics W2361 (DFP-1) contradicts itself:
(WW) Feb 03 19:12:37 NVIDIA(0):     mode "1024x768" is specified in the EDID; however, the
(WW) Feb 03 19:12:37 NVIDIA(0):     EDID's valid VertRefresh range (56.000-61.000 Hz) would
(WW) Feb 03 19:12:37 NVIDIA(0):     exclude this mode's VertRefresh (75.0 Hz); ignoring
(WW) Feb 03 19:12:37 NVIDIA(0):     VertRefresh check for mode "1024x768".
(II) Feb 03 19:12:37 NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(II) Feb 03 19:12:37 NVIDIA(0): Validated modes:
(II) Feb 03 19:12:37 NVIDIA(0):    
(II) Feb 03 19:12:37 NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:nvidia-auto-select+1600+0"
(II) Feb 03 19:12:37 NVIDIA(0): Virtual screen size determined to be 3520 x 1080
(--) Feb 03 19:12:38 NVIDIA(0): DPI set to (106, 108); computed from "UseEdidDpi" X config
(--) Feb 03 19:12:38 NVIDIA(0):     option
(==) Feb 03 19:12:38 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Feb 03 19:12:38 NVIDIA: Using 3069.00 MB of virtual memory for indirect memory
(II) Feb 03 19:12:38 NVIDIA:     access.
(II) Feb 03 19:12:38 NVIDIA(0): Initialized GPU GART.
(II) Feb 03 19:12:38 NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) Feb 03 19:12:38 NVIDIA(0):     enough to receive ACPI hotkey events.
(II) Feb 03 19:12:38 NVIDIA(0): ACPI brightness change hotkey events enabled.
(II) Feb 03 19:12:38 NVIDIA(0): Setting mode
(II) Feb 03 19:12:38 NVIDIA(0):     "DFP-0:nvidia-auto-select+0+0,DFP-1:nvidia-auto-select+1600+0"
(II) Loading extension NV-GLX
(II) Feb 03 19:12:38 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Feb 03 19:12:38 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled


```

---

### Post by lewys93 on 2011-08-12
I'm having the same problem, external displays are not recognised at all when connected via HDMI.

Is there anywhere I can get guidance on manually adding displays to the xorg.conf file? The documentation I've found only concerns Intel integrated graphics, it seems.
(Sorry to bump such an old thread, but it's better than starting a new one)

---

### Post by arpoodle on 2011-08-12
I'm afraid I can't help with your request, but your bump did remind me to post my resolution.

it seemed that the HDMI cable isn't quite the same at both ends.  I don't know what the difference is, but I examined the connector again and felt the connection into the laptop wasn't as secure as I'd have liked.  Out of interest, I tried the other end and it started working fine.

Sorry there's not a more technical, nor easily replicated resolution.

---

### Post by lewys93 on 2011-08-12
> **arpoodle said:**
> I'm afraid I can't help with your request, but your bump did remind me to post my resolution.

it seemed that the HDMI cable isn't quite the same at both ends.  I don't know what the difference is, but I examined the connector again and felt the connection into the laptop wasn't as secure as I'd have liked.  Out of interest, I tried the other end and it started working fine.

Sorry there's not a more technical, nor easily replicated resolution.

Ah right, at least I know when I do manage to add it, I'm unlikely to have the same colour problems as you because it was caused by your cable.


Just thought I'd add my xorg.conf file for reference as well, it seems to be pretty empty compared to yours:

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
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

Edit:
Just saved Xorg.conf through nvidia-settings, it's now as follows:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.41.03  (buildd@litembilla)  Mon Apr 11 20:45:06 UTC 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LGD"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 445M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```



Edit 2:

I just manually added my second display by adding parts from your xorg.conf file, but they don't seem to make any difference.

Edit 3:

After restarting, this did work. However, my external display cut off a lot of the workspace and it showed a separate desktop to the right of the one on my laptop's built-in display.

---

### Post by lewys93 on 2011-08-14
I've almost got it working now, but some of the screen is cut off on the external display. Is there any way to make the two displays (laptop and external) to display different resolutions (and if at all possible, turn the laptop's display off when the HDMI cable is connected)?

---


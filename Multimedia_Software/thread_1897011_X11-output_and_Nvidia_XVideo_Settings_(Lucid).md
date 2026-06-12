---
title: "X11-output and Nvidia XVideo Settings (Lucid)"
date: 2011-12-18
forum: Multimedia Software
---

### Post by crckhtlr on 2011-12-18
Hello all.  
  
 I've searched the internet like three times now, but cannot wrap my head around what my actual problem is. I mean, I know the problem but not really sure what's causing it.  

 I've GeForce 8800GTS, which so far has suited me just fine.  I previously had issues with screen tearing and got away with it installing Compiz, enabling Vsyncs all over and choosing x11 as the output in VLC. 
  
Then I bought a full hd projector and with it a weeks worth of head scratching and continuous smoking.   
  
See, I couldn't find any option for limited range video on Nvidia control panel (seeing as all(?) videos I wanna play are in 16-235 color space opposed to 0-255, so they appeared a little washed out). I found a workaround using avsforum's calibration vids and Nvidia's XVideo settings, which only affect video playback, so that the computer is feeding full range to my projector but the video still looks good. 
  
The thing is, with X11 output Nvidia's settings don't take place. With output to Xvideo I can change the brightness and contrast, but full hd video is just horrendous - laggy and glitchy with plenty screen tearing.  I dunno if it's because X11 is more CPU-hard option or what, but I managed to get it to playback really smooth and crisp. No tearing I can see, and with 'Skip the loop filter for h264' set to None, I get beautiful image on my screen too. That is, except that it's washed out since Nvidia's video settings won't affect it.  I'm at lost and frankly quite frustrated. Do you guys have any ideas?  cheers  -j

---

### Post by BicyclerBoy on 2011-12-18
The 8800GTS has no VDPAU, is a good old gaming card but GT430 is far better HTPC card.

So all your decoding/post processing is happening on CPU. Your GPU can scale/colorspace convert/overlay.

What's the CPU?

Driver settings for limited colour-space is an option for my DVI monitor (RGB only).
YUV encoding is possible over HDMI & DVI if monitor supports.
If your monitor supports YUV video then nVidia-settings will show this option & colour-space/range.

But the colour-space should be converted okay from anything to full range RGB (normal PC monitor). VLC must be screwing up..

Television video devices like projectors & CRTs expect limited range. VDPAU allows colour-space correction/overrides.
I use RGB VGA limited range with VDPAU.

X11 video is deprecated you should be using openGL or XVideo or better VDPAU.

You mention compiz composite ...if you are using 11.04 or 11.10 this can be problematic..Try [l,x]ubuntu desktop session.

VLC does not support VDPAU directly only thru' VAAPI.

Does the projector have HDMI ?
What nVidia driver version ?

What's in the /var/log/Xorg.0.log ?

---

### Post by crckhtlr on 2011-12-19
Yo, thanks for the reply :) 
 
 I've dual core 2,66GHz with 2 gig memory. You know, not the hottest computer on earth, but it has suited me just fine so far and at least X11 is playing full hd files pretty much without a glitch.

 The weird thing is I can't find any color/video range settings on my nVidia panel, even though I keep hearing they do exist somewhere, on somebody's computer at least :P  I'm updating drivers thru Hardware Drivers menu on System tab (Ubuntu 10.04), so I'm using version current.  NVidia Settings says 195.36.24.

 My projector is hooked via DVI-HDMI connector (I don't have an HDMI-out on my 8800GTS obviously), and it does accept full range (there's a switch in the menu). Full range on games looks quite fantastic really, but I need to be able to feed the projector limited range on videos cause they are not 0-255 and thus get washed out a bit.  

  I have surely something wrong with my settings, cause like I said, every other output option besides X11 on VLC (or Smplayer for that matter) is jerky and messy. I just checked and seems I've lost OpenGL output for some reason.  Yes, I'm a bit noobish when it comes dealing with in-depth video settings, so I must've done something wrong here :D 

Compiz I only installed back in the day for getting rid of the screen tearing.  I just tried a full-hd movie only on my 21' monitor. Using XVideo and switching back and forth from full screen to windowed, I can see CPU peaking at 100% every time I fullscreen it. With X11 both CPU's are around 50% :P

Here's the log, hope you can find some answers there (I sure as hell dunno what I'm even looking for):


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux jussi-desktop 2.6.32-36-generic #79-Ubuntu SMP Tue Nov 8 22:29:53 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-36-generic root=UUID=9ab3ebea-3a70-4e34-affa-7ab7d4d6691a ro quiet splash
Build Date: 20 October 2011  03:03:02PM
xorg-server 2:1.7.6-2ubuntu7.10 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 19 22:06:07 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
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

(--) PCI:*(0:2:0:0) 10de:0193:1682:2252 nVidia Corporation G80 [GeForce 8800 GTS] rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/131072
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
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
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
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
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
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT: nvidia-auto-select +0+0"
(**) Dec 19 22:06:07 NVIDIA(0): Enabling RENDER acceleration
(II) Dec 19 22:06:07 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Dec 19 22:06:07 NVIDIA(0):     enabled.
(II) Dec 19 22:06:08 NVIDIA(0): NVIDIA GPU GeForce 8800 GTS (G80) at PCI:2:0:0 (GPU-0)
(--) Dec 19 22:06:08 NVIDIA(0): Memory: 327680 kBytes
(--) Dec 19 22:06:08 NVIDIA(0): VideoBIOS: 60.80.18.00.90
(II) Dec 19 22:06:08 NVIDIA(0): Detected PCI Express Link width: 4X
(--) Dec 19 22:06:08 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Dec 19 22:06:08 NVIDIA(0): Connected display device(s) on GeForce 8800 GTS at PCI:2:0:0:
(--) Dec 19 22:06:08 NVIDIA(0):     LG L225W (CRT-1)
(--) Dec 19 22:06:08 NVIDIA(0): LG L225W (CRT-1): 400.0 MHz maximum pixel clock
(II) Dec 19 22:06:08 NVIDIA(0): Display Device found referenced in MetaMode: CRT-1
(II) Dec 19 22:06:08 NVIDIA(0): Assigned Display Device: CRT-1
(II) Dec 19 22:06:08 NVIDIA(0): Validated modes:
(II) Dec 19 22:06:08 NVIDIA(0):     "CRT:nvidia-auto-select+0+0"
(II) Dec 19 22:06:08 NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) Dec 19 22:06:08 NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
(--) Dec 19 22:06:08 NVIDIA(0):     option
(==) Dec 19 22:06:08 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "DFP: 1920x1080 +0+0"
(**) Dec 19 22:06:08 NVIDIA(1): Enabling RENDER acceleration
(II) Dec 19 22:06:08 NVIDIA(1): NVIDIA GPU GeForce 8800 GTS (G80) at PCI:2:0:0 (GPU-0)
(--) Dec 19 22:06:08 NVIDIA(1): Memory: 327680 kBytes
(--) Dec 19 22:06:08 NVIDIA(1): VideoBIOS: 60.80.18.00.90
(II) Dec 19 22:06:08 NVIDIA(1): Detected PCI Express Link width: 4X
(--) Dec 19 22:06:08 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Dec 19 22:06:08 NVIDIA(1): Connected display device(s) on GeForce 8800 GTS at PCI:2:0:0:
(--) Dec 19 22:06:08 NVIDIA(1):     LG L225W (CRT-1)
(--) Dec 19 22:06:08 NVIDIA(1): LG L225W (CRT-1): 400.0 MHz maximum pixel clock
(EE) Dec 19 22:06:08 NVIDIA(1): Unable to find available Display Devices for screen 1.
(EE) Dec 19 22:06:08 NVIDIA(1): No display devices found for this X screen.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(II) Dec 19 22:06:09 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Dec 19 22:06:09 NVIDIA(0): Initialized GPU GART.
(II) Dec 19 22:06:09 NVIDIA(0): Setting mode "CRT:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) Dec 19 22:06:09 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Dec 19 22:06:09 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
(II) Initializing extension GLX
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
(**) Option "xkb_layout" "fi"
(**) Option "xkb_variant" "classic"
(II) XKB: reuse xkmfile /var/lib/xkb/server-B810939095C0CD61AC8DAFD928C515F55FF5BF36.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(**) Option "xkb_variant" "classic"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "fi"
(**) Option "xkb_variant" "classic"
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event5)
(**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Logitech Wheel Mouse: Found relative axes
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse1)
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


Any ideas?

Cheers

-j

---

### Post by BicyclerBoy on 2011-12-19
There may be some old cruft in the /etc/X11/xorg.conf file but it does not seems to be doing any real harm.
You could post that file ..

The log file shows one VGA monitor connected.
VGA does not allow YUV nor reduced range colour-space in the voltage output.
Colour-space can set by the decoding process (YUV-->RGB conversion).

Don't confuse the colour-space of the link with the colour-space used by the encoded video..
SD & HD have difference colour-space etc..

Do you have desktop effects enabled (composite) ? (this does not mean just compiz installed).

glxinfo | grep OpenGL
glxgears

I have found compiz on 10.04 with nVidia separate X screens (no twinview) to behave okay (XVideo & VDPAU). But many have not..

Currently using nVidia 275 on lucid from a ppa..I suspect version 260 VDPAU was better..

A core2duo should handle HD H264 decode okay.

I seem to recall that the early drivers only showed the colour-space setting for HDMI YUV displays..
But if the display is set to match the video card setting there should be very little difference. YUV is a good improvement for contrast/blacks.

---

### Post by crckhtlr on 2011-12-20
Right. I had taken that log-file after I quickly turned on the comp without the projector - my bad :P

BUT: being a slow thinker I just now had the epiphany of trying another type of file for demo purposes, and it seems that even though xvideo does still give me really jarring screen tearing, at least I can playback .mkv's rather smoothly with it. Only mp4's give me that sorta juttering and continuous skipped frames. So it's a codec thing, it seems, afterall. Though both movies were in h264 format I think (as far as I know about this stuff). Playing back mp4's with Xvideo-output makes the player(s) really unresponsive too (takes seconds to get into menu or to pause the video etc), but mkv's are as smooth as played back with X11 - at least on a quick glimpse. Any good tips I should try next, or codec-packs I need to have? Still wondering about the lost OpenGL-option, cause I'm quite sure I had it before. And do you have any wild guesses why Vsync isn't helping with XVideo's tearing when it clearly works with X11?

Glxgears worked just fine, the former command gives me this just:

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8800 GTS/PCI/SSE2
OpenGL version string: 3.2.0 NVIDIA 195.36.24
OpenGL shading language version string: 1.50 NVIDIA via Cg compiler
OpenGL extensions:
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8800 GTS/PCI/SSE2
OpenGL version string: 3.2.0 NVIDIA 195.36.24
OpenGL shading language version string: 1.50 NVIDIA via Cg compiler
OpenGL extensions

Compiz desktop effects I've never used, so they are disabled, yeah.

But hey! I think I'm a couple steps closer to being quite a satisfied Ubuntian videophile :D - once this is done, I'm gotta attack the neverending sound issues :P

[edit]

Oh, and one question mark more: the video settings I made in nVidia's control panel (brightness and contrast) don't stick. I noticed this when I again played one of the calibration vids I have again and couldn't get good white levels even though I had just calibrated 'em. When I opened nVidia server settings, the right levels just popped in their place again o_O

j

---

### Post by BicyclerBoy on 2011-12-20
You could check that your 'user' is a member of the video group.

The nVidia-settings config stuff that does not belong in the Xorg /etc/X11/xorg.conf file end up in: 
~/.nvidia-setting-rc

Have a look in that file to check if your settings stick..

XVideo has a separate vsync tickbox to that of OpenGL, it is on another tab.
If you are using separate X screens (you are) you have to set the vsync for each separate screen. The video modes/rates are independent.

You could update the driver to 260 from xorg-edgers or x-swat team ppa.

I do not use VLC put it is still installed...
The stock VLC in 10.04 is a bit dated, but I have no problem playing H264 HD (broadcast OTA) with yadifx2 on a core2duo.
It does not match VDPAU feature set C playback but it's okay.

You can't use the container type (mkv, mpeg4, mpeg2-ts/ps, avi) as a gauge of the video codec used. But there are normal use defaults..
For example, mkv can contain anything because it is open-source standard, AVI's are just unspeakable..

You can use:
ffmpeg -i filename
mediainfo filename

mediainfo will bury you in information.

---

### Post by crckhtlr on 2011-12-21
I wasn't a user of the video group, but now am. Dunno if it made any difference tho?

The nVidia settings were there on the file, but had to be popped in again by opening the control panel. Weird. And yeah, I've ticked all boxes related to vsyncing. Still there's a bloody resilient screen tearing on top of the picture with XVideo out, no tearing whatsoever with x11 o_O

I updated my VLC awhile back hoping it'd solve one audio issue (it didn't). And ffmpeg just confirmed what I managed to dig out of VLC and SMplayer yesterday - both the .mkv ja .mp4 contained h264 and SMplayer is even using the same codec for both files. Still: bad bad stuttering on the .mp4, smooth playback on .mkv.

I must be missing some key component/codec/a whatsamathingie here, but since I haven't had to tackle these sorta issues pretty much since I got my Ubuntu up and running, I can't even remember what codecs or other video related stuff I've had to install then. And I'm just taking stabs in the dark pretty much.

Makes me wanna buy a Mac - almost :D

I'll try and have the time to update the nVidia driver tomorrow (quite a busy day today). Since I'm usually getting updates from System -> Admin -> Hardware Drivers, can I just go and get the update from ppa or do I gotta clean something up first?

---


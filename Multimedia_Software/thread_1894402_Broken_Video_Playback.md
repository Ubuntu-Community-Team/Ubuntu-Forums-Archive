---
title: "Broken Video Playback"
date: 2011-12-12
forum: Multimedia Software
---

### Post by Dan Again on 2011-12-12
My systems seems to be unable, or at least unwilling, to play video. I was trying to fix a problem with Banshee (crash on switch to "Now Playing" screen) and found something that suggesting typing...

XLIB_SKIP_ARGB_VISUALS=1

in a terminal. I also noticed updates to xorg edgers right before this, so I'm not really sure what the problem is.

When I try to open DRIconf I get the following message...

Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode.

I'm using an i3 processor with onboard graphics. Here's some more info...


dan@MediaCenter:~$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.12-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
dan@MediaCenter:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  0 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
i915                  566827  2 
drm_kms_helper         42558  1 i915
drm                   236290  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41480  0 
video                  19412  1 i915
snd                    68266  10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17693  0 
psmouse                73882  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
serio_raw              13166  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 

Can anyone help me?

---

### Post by Dan Again on 2011-12-13
Bump

---

### Post by BicyclerBoy on 2011-12-13
You are using the software rasterizer..

The video driver should be i915/i965
The vendor should be Tungsten Graphics etc
The render Mesa DRI Intel(R) etc

Can you define exactly which i3 ? pre-sandy, sandy or Ivy? (err Ivy not avail yet)
Good performance on these GPU requires kernel >= 3.0 & xorg-edgers ppa.

Post your /var/log/Xorg.0.log file ...maybe the GLX/DRI modules fail to load.

Could just try reinstall/re-configure xserver-xorg

---

### Post by Dan Again on 2011-12-13
First of all, thank you VERY much Bicycle...you've responded to several of my posts and have been very helpful. I really appreciate your knowledge and willingness to share it.

I tried to reinstall/reconfigure x with the following...

sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg

That didn't seem to change anything. Basically, when I open a video file, Totem opens and I hear the sound, but no video. Usually, the display will turn black for about 2-3 seconds every 2-3 seconds. When the screen is black, no sounds comes out.

Here is the what I found in /var/log/Xorg.O.log

[    17.302] 
X.Org X Server 1.11.2.902 (1.11.3 RC 2)
Release Date: 2011-12-09
[    17.302] X Protocol Version 11, Revision 0
[    17.302] Build Operating System: Linux 2.6.24-30-xen x86_64 Ubuntu
[    17.302] Current Operating System: Linux MediaCenter 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
[    17.302] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-14-generic root=UUID=a576999f-8cae-44d5-b60a-a5fcd072ab53 ro quiet splash vt.handoff=7
[    17.302] Build Date: 10 December 2011  08:30:20PM
[    17.302] xorg-server 2:1.11.2.902+git20111209+server-1.11-branch.0ca8869e-0ubuntu0sarvatt~oneiric (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    17.302] Current version of pixman: 0.24.0
[    17.302] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    17.302] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.302] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 13 20:32:05 2011
[    17.303] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.303] (==) No Layout section.  Using the first Screen section.
[    17.303] (==) No screen section available. Using defaults.
[    17.303] (**) |-->Screen "Default Screen Section" (0)
[    17.303] (**) |   |-->Monitor "<default monitor>"
[    17.303] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    17.303] (==) Automatically adding devices
[    17.303] (==) Automatically enabling devices
[    17.303] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.303] 	Entry deleted from font path.
[    17.303] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    17.303] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.303] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.303] (II) Loader magic: 0x7ceae0
[    17.303] (II) Module ABI versions:
[    17.303] 	X.Org ANSI C Emulation: 0.4
[    17.303] 	X.Org Video Driver: 11.0
[    17.303] 	X.Org XInput driver : 13.0
[    17.303] 	X.Org Server Extension : 6.0
[    17.303] (--) PCI:*(0:0:2:0) 8086:0102:1565:110d rev 9, Mem @ 0xfe000000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[    17.303] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.304] (II) LoadModule: "extmod"
[    17.315] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.315] (II) Module extmod: vendor="X.Org Foundation"
[    17.315] 	compiled for 1.11.2.902, module version = 1.0.0
[    17.315] 	Module class: X.Org Server Extension
[    17.315] 	ABI class: X.Org Server Extension, version 6.0
[    17.315] (II) Loading extension MIT-SCREEN-SAVER
[    17.315] (II) Loading extension XFree86-VidModeExtension
[    17.315] (II) Loading extension XFree86-DGA
[    17.315] (II) Loading extension DPMS
[    17.315] (II) Loading extension XVideo
[    17.315] (II) Loading extension XVideo-MotionCompensation
[    17.315] (II) Loading extension X-Resource
[    17.315] (II) LoadModule: "dbe"
[    17.315] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.315] (II) Module dbe: vendor="X.Org Foundation"
[    17.315] 	compiled for 1.11.2.902, module version = 1.0.0
[    17.315] 	Module class: X.Org Server Extension
[    17.315] 	ABI class: X.Org Server Extension, version 6.0
[    17.315] (II) Loading extension DOUBLE-BUFFER
[    17.315] (II) LoadModule: "glx"
[    17.315] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.315] (II) Module glx: vendor="X.Org Foundation"
[    17.315] 	compiled for 1.11.2.902, module version = 1.0.0
[    17.315] 	ABI class: X.Org Server Extension, version 6.0
[    17.315] (==) AIGLX enabled
[    17.315] (II) Loading extension GLX
[    17.315] (II) LoadModule: "record"
[    17.315] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.315] (II) Module record: vendor="X.Org Foundation"
[    17.315] 	compiled for 1.11.2.902, module version = 1.13.0
[    17.315] 	Module class: X.Org Server Extension
[    17.315] 	ABI class: X.Org Server Extension, version 6.0
[    17.315] (II) Loading extension RECORD
[    17.315] (II) LoadModule: "dri"
[    17.316] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.316] (II) Module dri: vendor="X.Org Foundation"
[    17.316] 	compiled for 1.11.2.902, module version = 1.0.0
[    17.316] 	ABI class: X.Org Server Extension, version 6.0
[    17.316] (II) Loading extension XFree86-DRI
[    17.316] (II) LoadModule: "dri2"
[    17.316] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.316] (II) Module dri2: vendor="X.Org Foundation"
[    17.316] 	compiled for 1.11.2.902, module version = 1.2.0
[    17.316] 	ABI class: X.Org Server Extension, version 6.0
[    17.316] (II) Loading extension DRI2
[    17.316] (==) Matched intel as autoconfigured driver 0
[    17.316] (==) Matched vesa as autoconfigured driver 1
[    17.316] (==) Matched fbdev as autoconfigured driver 2
[    17.316] (==) Assigned the driver to the xf86ConfigLayout
[    17.316] (II) LoadModule: "intel"
[    17.316] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.316] (II) Module intel: vendor="X.Org Foundation"
[    17.316] 	compiled for 1.11.2.902, module version = 2.17.0
[    17.316] 	Module class: X.Org Video Driver
[    17.316] 	ABI class: X.Org Video Driver, version 11.0
[    17.316] (II) LoadModule: "vesa"
[    17.316] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.316] (II) Module vesa: vendor="X.Org Foundation"
[    17.316] 	compiled for 1.11.2, module version = 2.3.0
[    17.316] 	Module class: X.Org Video Driver
[    17.316] 	ABI class: X.Org Video Driver, version 11.0
[    17.316] (II) LoadModule: "fbdev"
[    17.316] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.317] (II) Module fbdev: vendor="X.Org Foundation"
[    17.317] 	compiled for 1.11.2, module version = 0.4.2
[    17.317] 	Module class: X.Org Video Driver
[    17.317] 	ABI class: X.Org Video Driver, version 11.0
[    17.317] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    17.317] (II) VESA: driver for VESA chipsets: vesa
[    17.317] (II) FBDEV: driver for framebuffer: fbdev
[    17.317] (++) using VT number 7

[    17.318] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.318] (WW) Falling back to old probe method for vesa
[    17.318] (WW) Falling back to old probe method for fbdev
[    17.318] (II) Loading sub module "fbdevhw"
[    17.318] (II) LoadModule: "fbdevhw"
[    17.318] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.318] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.318] 	compiled for 1.11.2.902, module version = 0.0.2
[    17.318] 	ABI class: X.Org Video Driver, version 11.0
[    17.318] drmOpenDevice: node name is /dev/dri/card0
[    17.318] drmOpenDevice: open result is 12, (OK)
[    17.318] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    17.318] drmOpenDevice: node name is /dev/dri/card0
[    17.318] drmOpenDevice: open result is 12, (OK)
[    17.318] drmOpenByBusid: drmOpenMinor returns 12
[    17.318] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    17.318] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    17.318] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    17.318] (==) intel(0): RGB weight 888
[    17.318] (==) intel(0): Default visual is TrueColor
[    17.318] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[    17.318] (--) intel(0): Chipset: "Sandybridge Desktop (GT1)"
[    17.318] (**) intel(0): Relaxed fencing enabled
[    17.318] (**) intel(0): Wait on SwapBuffers? enabled
[    17.318] (**) intel(0): Triple buffering? enabled
[    17.318] (**) intel(0): Framebuffer tiled
[    17.318] (**) intel(0): Pixmaps tiled
[    17.318] (**) intel(0): 3D buffers tiled
[    17.318] (**) intel(0): SwapBuffers wait enabled
[    17.318] (==) intel(0): video overlay key set to 0x101fe
[    17.318] (II) intel(0): Output VGA1 has no monitor section
[    17.344] (II) intel(0): Output HDMI1 has no monitor section
[    17.392] (II) intel(0): Output DP1 has no monitor section
[    17.666] (II) intel(0): Output HDMI2 has no monitor section
[    17.712] (II) intel(0): Output DP2 has no monitor section
[    17.712] (II) intel(0): EDID for output VGA1
[    17.736] (II) intel(0): EDID for output HDMI1
[    17.784] (II) intel(0): EDID for output DP1
[    18.050] (II) intel(0): EDID for output HDMI2
[    18.050] (II) intel(0): Manufacturer: HSP  Model: 2a  Serial#: 520
[    18.050] (II) intel(0): Year: 2010  Week: 15
[    18.050] (II) intel(0): EDID Version: 1.3
[    18.050] (II) intel(0): Digital Display Input
[    18.050] (II) intel(0): Max Image Size [cm]: horiz.: 93  vert.: 52
[    18.050] (II) intel(0): Gamma: 2.20
[    18.050] (II) intel(0): DPMS capabilities: Off
[    18.050] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.050] (II) intel(0): First detailed timing is preferred mode
[    18.050] (II) intel(0): redX: 0.649 redY: 0.334   greenX: 0.267 greenY: 0.610
[    18.050] (II) intel(0): blueX: 0.149 blueY: 0.060   whiteX: 0.280 whiteY: 0.285
[    18.050] (II) intel(0): Supported established timings:
[    18.050] (II) intel(0): 640x480@60Hz
[    18.050] (II) intel(0): 800x600@60Hz
[    18.050] (II) intel(0): 1024x768@60Hz
[    18.050] (II) intel(0): Manufacturer's mask: 0
[    18.050] (II) intel(0): Supported standard timings:
[    18.050] (II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    18.050] (II) intel(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    18.050] (II) intel(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    18.050] (II) intel(0): Supported detailed timing:
[    18.050] (II) intel(0): clock: 148.5 MHz   Image Size:  930 x 523 mm
[    18.050] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    18.050] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    18.050] (II) intel(0): Serial No: 015YG24Y00520
[    18.050] (II) intel(0): Monitor name: HSG1102
[    18.050] (II) intel(0): Ranges: V min: 59 V max: 61 Hz, H min: 31 H max: 70 kHz, PixClock max 155 MHz
[    18.050] (II) intel(0): Supported detailed timing:
[    18.050] (II) intel(0): clock: 148.5 MHz   Image Size:  930 x 523 mm
[    18.050] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    18.050] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    18.050] (II) intel(0): Supported detailed timing:
[    18.050] (II) intel(0): clock: 74.2 MHz   Image Size:  930 x 523 mm
[    18.050] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    18.050] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    18.050] (II) intel(0): Supported detailed timing:
[    18.050] (II) intel(0): clock: 27.0 MHz   Image Size:  930 x 523 mm
[    18.050] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    18.050] (II) intel(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    18.050] (II) intel(0): Supported detailed timing:
[    18.050] (II) intel(0): clock: 74.2 MHz   Image Size:  930 x 523 mm
[    18.050] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    18.050] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    18.050] (II) intel(0): Number of EDID sections to follow: 1
[    18.050] (II) intel(0): EDID (in hex):
[    18.050] (II) intel(0): 	00ffffffffffff0022702a0008020000
[    18.050] (II) intel(0): 	0f140103805d34782a655ca655449c26
[    18.050] (II) intel(0): 	0f474921080081809500b30001010101
[    18.050] (II) intel(0): 	010101010101023a801871382d40582c
[    18.050] (II) intel(0): 	4500a20b3200001e000000ff00303135
[    18.050] (II) intel(0): 	59473234593030353230000000fc0048
[    18.050] (II) intel(0): 	5347313130320a2020202020000000fd
[    18.050] (II) intel(0): 	003b3d1f460f000a20202020202001ee
[    18.050] (II) intel(0): 	02031e71480102030405060790260907
[    18.050] (II) intel(0): 	071107508301000065030c002000023a
[    18.050] (II) intel(0): 	801871382d40582c4500a20b3200001e
[    18.050] (II) intel(0): 	011d8018711c1620582c2500a20b3200
[    18.050] (II) intel(0): 	009e8c0ad08a20e02d10103e9600a20b
[    18.050] (II) intel(0): 	32000018011d007251d01e206e285500
[    18.050] (II) intel(0): 	a20b3200001e00000000000000000000
[    18.050] (II) intel(0): 	0000000000000000000000000000008d
[    18.050] (II) intel(0): Printing probed modes for output HDMI2
[    18.050] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    18.050] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    18.050] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.050] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    18.050] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.050] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.050] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.096] (II) intel(0): EDID for output DP2
[    18.096] (II) intel(0): Output VGA1 disconnected
[    18.096] (II) intel(0): Output HDMI1 disconnected
[    18.096] (II) intel(0): Output DP1 disconnected
[    18.096] (II) intel(0): Output HDMI2 connected
[    18.096] (II) intel(0): Output DP2 disconnected
[    18.096] (II) intel(0): Using exact sizes for initial modes
[    18.096] (II) intel(0): Output HDMI2 using initial mode 1920x1080
[    18.096] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.096] (II) intel(0): Kernel page flipping support detected, enabling
[    18.096] (==) intel(0): DPI set to (96, 96)
[    18.096] (II) Loading sub module "fb"
[    18.096] (II) LoadModule: "fb"
[    18.096] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.096] (II) Module fb: vendor="X.Org Foundation"
[    18.096] 	compiled for 1.11.2.902, module version = 1.0.0
[    18.096] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.096] (II) Loading sub module "dri2"
[    18.096] (II) LoadModule: "dri2"
[    18.096] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.096] (II) Module dri2: vendor="X.Org Foundation"
[    18.096] 	compiled for 1.11.2.902, module version = 1.2.0
[    18.096] 	ABI class: X.Org Server Extension, version 6.0
[    18.096] (II) UnloadModule: "vesa"
[    18.096] (II) Unloading vesa
[    18.096] (II) UnloadModule: "fbdev"
[    18.096] (II) Unloading fbdev
[    18.096] (II) UnloadModule: "fbdevhw"
[    18.096] (II) Unloading fbdevhw
[    18.096] (==) Depth 24 pixmap format is 32 bpp
[    18.096] (II) intel(0): [DRI2] Setup complete
[    18.096] (II) intel(0): [DRI2]   DRI driver: i965
[    18.096] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[    18.097] (II) UXA(0): Driver registered support for the following operations:
[    18.097] (II)         solid
[    18.097] (II)         copy
[    18.097] (II)         composite (RENDER acceleration)
[    18.097] (II)         put_image
[    18.097] (II)         get_image
[    18.097] (==) intel(0): Backing store disabled
[    18.097] (==) intel(0): Silken mouse enabled
[    18.097] (II) intel(0): Initializing HW Cursor
[    18.156] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.156] (==) intel(0): DPMS enabled
[    18.156] (==) intel(0): Intel XvMC decoder enabled
[    18.156] (II) intel(0): Set up textured video
[    18.156] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    18.156] (II) intel(0): direct rendering: DRI2 Enabled
[    18.156] (==) intel(0): hotplug detection: "enabled"
[    18.156] (--) RandR disabled
[    18.156] (II) Initializing built-in extension Generic Event Extension
[    18.156] (II) Initializing built-in extension SHAPE
[    18.156] (II) Initializing built-in extension MIT-SHM
[    18.156] (II) Initializing built-in extension XInputExtension
[    18.156] (II) Initializing built-in extension XTEST
[    18.156] (II) Initializing built-in extension BIG-REQUESTS
[    18.156] (II) Initializing built-in extension SYNC
[    18.156] (II) Initializing built-in extension XKEYBOARD
[    18.156] (II) Initializing built-in extension XC-MISC
[    18.156] (II) Initializing built-in extension SECURITY
[    18.156] (II) Initializing built-in extension XINERAMA
[    18.156] (II) Initializing built-in extension XFIXES
[    18.156] (II) Initializing built-in extension RENDER
[    18.156] (II) Initializing built-in extension RANDR
[    18.156] (II) Initializing built-in extension COMPOSITE
[    18.156] (II) Initializing built-in extension DAMAGE
[    18.160] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
[    18.167] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.167] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.167] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.167] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.167] (II) AIGLX: Loaded and initialized i965
[    18.167] (II) GLX: Initialized DRI2 GL provider for screen 0
[    18.167] (II) intel(0): Setting screen physical size to 508 x 285
[    18.177] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.179] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.179] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.179] (II) LoadModule: "evdev"
[    18.179] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.179] (II) Module evdev: vendor="X.Org Foundation"
[    18.179] 	compiled for 1.11.2.901, module version = 2.6.99
[    18.179] 	Module class: X.Org XInput Driver
[    18.179] 	ABI class: X.Org XInput driver, version 13.0
[    18.179] (II) Using input driver 'evdev' for 'Power Button'
[    18.179] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.179] (**) Power Button: always reports core events
[    18.179] (**) evdev: Power Button: Device: "/dev/input/event1"
[    18.179] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.179] (--) evdev: Power Button: Found keys
[    18.179] (II) evdev: Power Button: Configuring as keyboard
[    18.179] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    18.179] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.179] (**) Option "xkb_rules" "evdev"
[    18.179] (**) Option "xkb_model" "pc105"
[    18.179] (**) Option "xkb_layout" "us"
[    18.179] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.179] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.179] (II) Using input driver 'evdev' for 'Power Button'
[    18.179] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.179] (**) Power Button: always reports core events
[    18.179] (**) evdev: Power Button: Device: "/dev/input/event0"
[    18.179] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.179] (--) evdev: Power Button: Found keys
[    18.179] (II) evdev: Power Button: Configuring as keyboard
[    18.179] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    18.179] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    18.179] (**) Option "xkb_rules" "evdev"
[    18.179] (**) Option "xkb_model" "pc105"
[    18.179] (**) Option "xkb_layout" "us"
[    18.179] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event5)
[    18.179] (II) No input driver/identifier specified (ignoring)
[    18.180] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event6)
[    18.180] (II) No input driver/identifier specified (ignoring)
[    18.180] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event7)
[    18.180] (II) No input driver/identifier specified (ignoring)
[    18.180] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/event2)
[    18.180] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    18.180] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    18.180] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.180] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    18.180] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Device: "/dev/input/event2"
[    18.180] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Vendor 0x45e Product 0x745
[    18.180] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found keys
[    18.180] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Configuring as keyboard
[    18.180] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input2/event2"
[    18.180] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: KEYBOARD, id 8)
[    18.180] (**) Option "xkb_rules" "evdev"
[    18.180] (**) Option "xkb_model" "pc105"
[    18.180] (**) Option "xkb_layout" "us"
[    18.180] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/event3)
[    18.180] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev pointer catchall"
[    18.180] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    18.180] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    18.180] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.180] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    18.180] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Device: "/dev/input/event3"
[    18.180] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Vendor 0x45e Product 0x745
[    18.180] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found 9 mouse buttons
[    18.180] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found scroll wheel(s)
[    18.180] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found relative axes
[    18.180] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found x and y relative axes
[    18.180] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found absolute axes
[    18.180] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found keys
[    18.180] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Configuring as mouse
[    18.180] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Configuring as keyboard
[    18.180] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Adding scrollwheel support
[    18.180] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: YAxisMapping: buttons 4 and 5
[    18.181] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.181] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input3/event3"
[    18.181] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: KEYBOARD, id 9)
[    18.181] (**) Option "xkb_rules" "evdev"
[    18.181] (**) Option "xkb_model" "pc105"
[    18.181] (**) Option "xkb_layout" "us"
[    18.181] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: initialized for relative axes.
[    18.181] (WW) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: ignoring absolute axes.
[    18.181] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) keeping acceleration scheme 1
[    18.181] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration profile 0
[    18.181] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration factor: 2.000
[    18.181] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration threshold: 4
[    18.181] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/mouse0)
[    18.181] (II) No input driver/identifier specified (ignoring)
[    18.181] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/event4)
[    18.181] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: Applying InputClass "evdev keyboard catchall"
[    18.181] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v8.0'
[    18.181] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.181] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: always reports core events
[    18.181] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Device: "/dev/input/event4"
[    18.181] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Vendor 0x45e Product 0x745
[    18.181] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found 1 mouse buttons
[    18.181] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found scroll wheel(s)
[    18.181] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found relative axes
[    18.181] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found absolute axes
[    18.181] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found x and y absolute axes
[    18.181] (--) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Found keys
[    18.181] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Configuring as mouse
[    18.181] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Configuring as keyboard
[    18.181] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: Adding scrollwheel support
[    18.181] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: YAxisMapping: buttons 4 and 5
[    18.181] (**) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.181] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.2/input/input4/event4"
[    18.181] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v8.0" (type: KEYBOARD, id 10)
[    18.181] (**) Option "xkb_rules" "evdev"
[    18.181] (**) Option "xkb_model" "pc105"
[    18.181] (**) Option "xkb_layout" "us"
[    18.181] (EE) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: failed to initialize for relative axes.
[    18.181] (WW) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: found 37 axes, limiting to 36.
[    18.181] (II) evdev: Microsoft Microsoft® 2.4GHz Transceiver v8.0: initialized for absolute axes.
[    18.182] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) keeping acceleration scheme 1
[    18.182] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration profile 0
[    18.182] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration factor: 2.000
[    18.182] (**) Microsoft Microsoft® 2.4GHz Transceiver v8.0: (accel) acceleration threshold: 4
[    18.182] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v8.0 (/dev/input/js0)
[    18.182] (II) No input driver/identifier specified (ignoring)
[    18.813] (II) intel(0): EDID vendor "HSP", prod id 42
[    18.813] (II) intel(0): Using EDID range info for horizontal sync
[    18.813] (II) intel(0): Using EDID range info for vertical refresh
[    18.813] (II) intel(0): Printing DDC gathered Modelines:
[    18.813] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    18.813] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    18.813] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    18.813] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    18.813] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.813] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.813] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.813] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.813] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    18.813] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    18.813] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    18.813] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    18.813] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    21.897] (II) intel(0): EDID vendor "HSP", prod id 42
[    21.897] (II) intel(0): Using hsync ranges from config file
[    21.897] (II) intel(0): Using vrefresh ranges from config file
[    21.897] (II) intel(0): Printing DDC gathered Modelines:
[    21.897] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    21.897] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    21.897] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    21.897] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    21.897] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.897] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.897] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.897] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    21.897] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    21.897] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    21.897] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    21.897] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    21.897] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    28.570] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[    29.217] (II) intel(0): EDID vendor "HSP", prod id 42
[    29.217] (II) intel(0): Using hsync ranges from config file
[    29.217] (II) intel(0): Using vrefresh ranges from config file
[    29.217] (II) intel(0): Printing DDC gathered Modelines:
[    29.217] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    29.217] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    29.217] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    29.217] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    29.217] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    29.217] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    29.217] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    29.217] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    29.217] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    29.217] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    29.217] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    29.217] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    29.217] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    29.729] (II) intel(0): EDID vendor "HSP", prod id 42
[    29.729] (II) intel(0): Using hsync ranges from config file
[    29.729] (II) intel(0): Using vrefresh ranges from config file
[    29.729] (II) intel(0): Printing DDC gathered Modelines:
[    29.729] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    29.729] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    29.729] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    29.729] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    29.729] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    29.729] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    29.729] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    29.729] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    29.729] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    29.729] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    29.729] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    29.729] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    29.729] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    29.779] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[    30.498] (II) intel(0): EDID vendor "HSP", prod id 42
[    30.498] (II) intel(0): Using hsync ranges from config file
[    30.498] (II) intel(0): Using vrefresh ranges from config file
[    30.498] (II) intel(0): Printing DDC gathered Modelines:
[    30.498] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    30.498] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    30.498] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    30.498] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    30.498] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    30.498] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    30.498] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    30.498] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    30.498] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    30.498] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    30.498] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    30.498] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    30.498] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    35.265] (II) intel(0): EDID vendor "HSP", prod id 42
[    35.265] (II) intel(0): Using hsync ranges from config file
[    35.265] (II) intel(0): Using vrefresh ranges from config file
[    35.265] (II) intel(0): Printing DDC gathered Modelines:
[    35.265] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    35.265] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    35.265] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    35.265] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    35.265] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.265] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.265] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.265] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.265] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    35.265] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    35.265] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    35.265] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    35.265] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    45.449] (II) intel(0): EDID vendor "HSP", prod id 42
[    45.449] (II) intel(0): Using hsync ranges from config file
[    45.449] (II) intel(0): Using vrefresh ranges from config file
[    45.449] (II) intel(0): Printing DDC gathered Modelines:
[    45.449] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    45.449] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    45.449] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    45.449] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    45.449] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    45.449] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    45.449] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    45.449] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    45.449] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    45.449] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    45.449] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    45.449] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    45.449] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    59.120] (EE) intel(0): Detected a hung GPU, disabling acceleration.
[    59.120] (EE) intel(0): When reporting this, please include i915_error_state from debugfs and the full dmesg.
[    89.233] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm

Thanks again...I really do appreciate it.

---

### Post by BicyclerBoy on 2011-12-14
It all looked fine except for the 2nd to last line..
GPU crashed
[ 59.120] (EE) intel(0): Detected a hung GPU, disabling acceleration.

Your xserver packages look to be up-to-date. (9/12/2011)
You're using xorg-edgers with 
[https://launchpad.net/~sarvatt/+archive/intel-sna](https://launchpad.net/~sarvatt/+archive/intel-sna)
to get sandybridge support ?

It has just jumped up to 20111212..

---

### Post by Dan Again on 2011-12-14
I added the intel-sna package and the problem is fixed! Thank you so much. I'm still having video tearing issues, though...any chance you could offer some more advice on how to resolve those?

---

### Post by BicyclerBoy on 2011-12-14
You can try
driconf & set sync to vertical blank.

Is your tearing on openGL or video playback ?
Are you using VAAPI ?

I would suspect unity/compiz composite is likely culprit.
You could install/run:
ccsm

Be very careful not to change too much but find openGL & composite tab & check/expt the vsync settings..
You may have to set composite refresh rate or 2xrefresh or to a fixed number & not auto..

If the desktop is broken beyond repair can run:
unity --reset

---

### Post by Dan Again on 2011-12-14
I have a driconf installed and believe I have set sync to vertical blank, but I'm not really positive. I am still getting the following error message when I open driconf...

Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode.

I'm not really sure what you mean vis-a-vis openGL or video playback. If I can could solve screen tearing in Totem (playing video files stored on my HD) I'd be happy. I don't know if I'm using VAAPI.

The system I am dealing with is a dedicated HTPC - I don't need it to have any special effects or really any capabilities other than basic internet access (for media streaming and downloading) and video/music playback. I've read in several places that Unity/Compiz are likely culprits of these problems. Is there a way I can turn them off? I have ccsm installed and have tinkered with it...I can make the problem a little better or worse, but have never really been able to "solve" it.

Are there any other terminal outputs or screen shots I could post that would be helpful?

---

### Post by BicyclerBoy on 2011-12-14
Could try deleting 
~/.drirc
file & restarting driconf..

Your desktop is drawn with openGL with the effects added by composite manager (mutter/clutter/metacity/compiz).
Unity is a compiz plugin..

Video playback is normally an overlay with h/w support. I believe DRI is used with intel.
Video decode in h/w is possible with VAAPI (intel, nVidia, AMD).

VAAPI is supported by intel driver (improving all the time) 
Run
vainfo
to check the install capabilities..
VAAPI is a very good thing for HTPC..but you need to use media player that supports it..
special build of VLC or XBMC.
Totem use gstreamer backend & I think it is possible to get it to work with VAAPI.

XBMC (& mythtv) are/have proper HTPC interfaces.. 

To try without compiz you could:
- login as unity 2d session.
-  install the gnome3 fallback (Gnome 3 made to approximate Gnome 2 Classic) package & then login as a gnome 3 session. This uses metacity for effects..

---

### Post by Dan Again on 2011-12-15
I tried deleting drirc as you suggested, but it didn't seem to work. Prior to deleting that file, when driconf would start in expert mode, there would still be lots of options and it seemed as if it was, in fact, configuring a device. Now when I start it, there are no options whatsoever, I tried adding a device, but didn't have much luck.

When I run vainfo I get the following message...

dan@MediaCenter:~$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

I did some research, but couldn't figure out how to fix this problem without restricted-drivers-manager.

---

### Post by BicyclerBoy on 2011-12-15
I suspect driconf was just changing the config file & never the h/w.
The xorg-edger's webpage recommended deleting that file at each upgrade..

It is possible driconf is out of sync with the SNA video driver..
The uber-users probably edit a config file directly.

Read thru' /var/log/Xorg.0.log for any errors..it is possible that DRI interface is still not working..

cat /var/log/Xorg.0.log | grep DRI
glxinfo | grep OpenGL

---

### Post by Dan Again on 2011-12-16
Here is the output from the terminal...


dan@MediaCenter:~$ cat /var/log/Xorg.0.log | grep DRI
[ 86198.327] (II) Loading extension XFree86-DRI
[ 86198.328] (II) Loading extension DRI2
[ 86199.101] (WW) intel(0): cannot enable DRI2 whilst the GPU is wedged
[ 86199.107] (II) AIGLX: Screen 0 is not DRI2 capable
[ 86199.108] (II) AIGLX: Screen 0 is not DRI capable
[ 86199.108] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
[ 86199.110] (II) GLX: Initialized DRISWRAST GL provider for screen 0
dan@MediaCenter:~$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.12-devel
OpenGL shading language version string: 1.20
OpenGL extensions:

---

### Post by BicyclerBoy on 2011-12-16
This is still a problem
[ 86199.101] (WW) intel(0): cannot enable DRI2 whilst the GPU is wedged
then the software rasterizer is loaded...

I guess you have to keep updating & hope..

There is the possibility of an additional  permissions problem with DRI.
The intel driver on 10.10/11.04 seems to need this in /etc/X11/xorg.conf:
```

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
#        Option          "AccelMethod" "UXA"
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
All it really does is set the video group & permissions...it may not be necessary anymore...

---


---
title: "No HDMI Output, mythbuntu 11.10"
date: 2012-04-09
forum: Mythbuntu
---

### Post by drewdin on 2012-04-09
I have a brand new build with 64bit .24fixes and Intel dh67bl motherboard that has HDMI output. I also have a tv that has an hdmi input, unfortunately all i get is a scrambled screen when i connect the hdmi cable.

If i use the display port, and the dvi to via adaptor i can get standard tv but the resolution is so low that HD looks real bad and is unwatchable. 

I was wondering if anyone had any experience with getting the hdmi working, when the pc boots, i can get into the bios and everything fine, its just when myth boots that i get a scrambled screen. 

I am guessing that it is a resolution issue but I'm not 100% sure. See attached screenshot of what my screen looks like and any help would be greatly appreciated! Thanks

---

### Post by dylan07 on 2012-04-09
post output of this:

press ctrl + alt + T and type:
```
xrandr -q
```

Post it in a code box.

---

### Post by drewdin on 2012-04-09
i was able to ssh in and get the output of Xorg.0.log its below:

X.Org X Server 1.10.4
Release Date: 2011-08-19
[     6.129] X Protocol Version 11, Revision 0
[     6.129] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     6.129] Current Operating System: Linux mythbackend 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64
[     6.129] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=5e6f1f30-7f29-4fe3-bd11-92fc59fbc13c ro quiet splash vt.handoff=7
[     6.129] Build Date: 19 October 2011  05:21:26AM
[     6.129] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[     6.129] Current version of pixman: 0.22.2
[     6.129]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[     6.129] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.129] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr  9 20:28:17 2012
[     6.130] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.130] (==) No Layout section.  Using the first Screen section.
[     6.130] (==) No screen section available. Using defaults.
[     6.130] (**) |-->Screen "Default Screen Section" (0)
[     6.130] (**) |   |-->Monitor "<default monitor>"
[     6.130] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[     6.130] (==) Automatically adding devices
[     6.130] (==) Automatically enabling devices
[     6.130] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.130]    Entry deleted from font path.

When i cntl+alt+t the screen never changes but using ssh i get

Can't open display 

I'm guessing thats because m ssh'd in.

---

### Post by drewdin on 2012-04-09
I also came across this post which is almost identical to what I am running, i am scared to start going towards .25 yet.

Any suggestions? Thanks

---

### Post by nickrout on 2012-04-10
ssh in```
export DISPLAY=:0
xrandr -q
xwininfo -root
```

The Xorg.0.log posted above is incomplete.

---

### Post by drewdin on 2012-04-10
I'll run that tonight, everything I had in the log I posted above. From what I have been reading I cant use Intel video becuase of the way it displays it.

Since .25 fixes that issue i might just upgrade and see if that fixes it, would you recommend to upgrade or not? Thanks

---

### Post by nickrout on 2012-04-10
I doubt whether 0.25 fixes an xorg problem, but you are welcome to try :)

---

### Post by drewdin on 2012-04-10
good point, everything i was reading is that it is an issue with Myth and Intel graphics and that .25 can display it while .24 could not. I was hoping that it would fix the issue but if it is an Xorg issue, i see what your saying.

Being a linux rookie, any suggestions on how to install the update? :)

---

### Post by drewdin on 2012-04-10
@nickrout, here is the info you requested. I appreciate your help and let me know if you need any other info!!

On the fuzzy screen it does say Z4 : Off

Screen 0: minimum 320 x 200, current 1280 x 720, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 connected 1280x720+0+0 (normal left inverted right x axis y axis) 952mm x 536mm
   1280x720       50.0*    60.0  
   720x480        59.9  
DP2 disconnected (normal left inverted right x axis y axis)

xwininfo: Window id: 0xab (the root window) (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1280
  Height: 720
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1280x720+0+0

---

### Post by drewdin on 2012-04-11
Did the above info help?

---

### Post by nickrout on 2012-04-11
It tells me that your X server is running at a reasonable resolution (1280x720).

It doesn't tell me why you are seeing strange things on your screen. I don't know too much about intel graphics, I am an nVidia man through and through.

Can you get any program up on the screen? The keyboard shortcut to get up a terminal is ctrl-alt-t. 

I see xrandr states it will also work at 720x480 - try ```
xrandr -s 720x480
```

Your Xorg.0.log is incomplete despite what you claim. I suspect that you only gave us the first screenful, your partial log isn't even up to the part where it detects your video card and what driver to use.

EDIT: the pic you posted appears to be upside down. Is that because I am in New Zealand?

---

### Post by drewdin on 2012-04-12
haha, the pic is upside down, I took the pic with my iphone. No matter what I do I cant get the darn thing rotated so i just posted it. I figured that even if it was upside down it might help.

Thanks for the help, im going to repost the Xorg.0.log tonight. 

Everything I have read reccommends using an NVIDIA videocard. I am checking out newegg right now for a slim videocard for HD, any recommendations?

Thanks Again!

---

### Post by drewdin on 2012-04-13
Here is my full Xorg.o.log file, you were correct, it was incomplete. If there is anything else you want to to try i would greatly appreciate it!


```
X.Org X Server 1.10.4
Release Date: 2011-08-19
[     5.405] X Protocol Version 11, Revision 0
[     5.405] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     5.405] Current Operating System: Linux mythbackend 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64
[     5.405] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=5e6f1f30-7f29-4fe3-bd11-92fc59fbc13c ro quiet splash vt.handoff=7
[     5.405] Build Date: 19 October 2011  05:21:26AM
[     5.405] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support)
[     5.405] Current version of pixman: 0.22.2
[     5.405]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[     5.405] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.405] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 13 23:00:08 2012
[     5.406] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.406] (==) No Layout section.  Using the first Screen section.
[     5.406] (==) No screen section available. Using defaults.
[     5.406] (**) |-->Screen "Default Screen Section" (0)
[     5.406] (**) |   |-->Monitor "<default monitor>"
[     5.406] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[     5.406] (==) Automatically adding devices
[     5.406] (==) Automatically enabling devices
[     5.406] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.406]    Entry deleted from font path.
[     5.406] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.406]    Entry deleted from font path.
[     5.406] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.406]    Entry deleted from font path.
[     5.406] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.406]    Entry deleted from font path.
[     5.406] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.406]    Entry deleted from font path.
[     5.410] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[     5.410]    Entry deleted from font path.
[     5.410]    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[     5.410] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[     5.410] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.410] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.410] (II) Loader magic: 0x7e0220
[     5.410] (II) Module ABI versions:
[     5.410]    X.Org ANSI C Emulation: 0.4
[     5.410]    X.Org Video Driver: 10.0
                                                              1,1           Top

```

---

### Post by drewdin on 2012-04-14
call me crazy but i also cannot seem to find an Xorg.conf file, it defiantly not in the /etc/X11/ folder.  Could that be whats going on or is it installed somewhere else on MythBuntu?

Also, when i tried 

xrandr -s 720x480

I got the same Cant Open Display

---

### Post by nickrout on 2012-04-14
> **drewdin said:**
> call me crazy but i also cannot seem to find an Xorg.conf file, it defiantly not in the /etc/X11/ folder.  Could that be whats going on or is it installed somewhere else on MythBuntu?

Also, when i tried 

xrandr -s 720x480

I got the same Cant Open Display

OK so you ran that via ssh? That's because when you ssh in the DISPLAY variable is not set. Try```
export DISPLAY=:0
``` then run your xrandr command.

If you don't have an xorg.conf (note the lack of capitalisation) it's because your system is auto configuring everything and thinks you don't need one. If you need to manually set something, just create an xorg.conf file in /etc/X11

Your Xorg.0.log is far from complete. Upload the whole file instead of pasting in part of it.

---

### Post by drewdin on 2012-04-15
Here is the file right from the myth box, Unfortunately i can't upload .log files so i changed the file to a text file. Then it was too big to be uplaoded so i just copied and pasted it again.

I appreciate the help and let me know if you need me to check anything else! 

```
[     6.086] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[     6.086] X Protocol Version 11, Revision 0
[     6.086] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     6.086] Current Operating System: Linux mythbackend 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64
[     6.086] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=5e6f1f30-7f29-4fe3-bd11-92fc59fbc13c ro quiet splash vt.handoff=7
[     6.086] Build Date: 19 October 2011  05:21:26AM
[     6.086] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[     6.086] Current version of pixman: 0.22.2
[     6.086] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     6.086] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.086] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 15 11:46:58 2012
[     6.087] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.087] (==) No Layout section.  Using the first Screen section.
[     6.087] (==) No screen section available. Using defaults.
[     6.087] (**) |-->Screen "Default Screen Section" (0)
[     6.087] (**) |   |-->Monitor "<default monitor>"
[     6.087] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     6.087] (==) Automatically adding devices
[     6.087] (==) Automatically enabling devices
[     6.087] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.087] 	Entry deleted from font path.
[     6.087] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.087] 	Entry deleted from font path.
[     6.087] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.087] 	Entry deleted from font path.
[     6.087] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.087] 	Entry deleted from font path.
[     6.087] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.087] 	Entry deleted from font path.
[     6.087] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[     6.087] 	Entry deleted from font path.
[     6.087] 	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[     6.087] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     6.087] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.087] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.087] (II) Loader magic: 0x7e0220
[     6.087] (II) Module ABI versions:
[     6.087] 	X.Org ANSI C Emulation: 0.4
[     6.087] 	X.Org Video Driver: 10.0
[     6.087] 	X.Org XInput driver : 12.3
[     6.087] 	X.Org Server Extension : 5.0
[     6.088] (--) PCI:*(0:0:2:0) 8086:0112:8086:2002 rev 9, Mem @ 0xfe000000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[     6.088] (II) Open ACPI successful (/var/run/acpid.socket)
[     6.088] (II) LoadModule: "extmod"
[     6.089] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     6.089] (II) Module extmod: vendor="X.Org Foundation"
[     6.089] 	compiled for 1.10.4, module version = 1.0.0
[     6.089] 	Module class: X.Org Server Extension
[     6.089] 	ABI class: X.Org Server Extension, version 5.0
[     6.089] (II) Loading extension MIT-SCREEN-SAVER
[     6.089] (II) Loading extension XFree86-VidModeExtension
[     6.089] (II) Loading extension XFree86-DGA
[     6.089] (II) Loading extension DPMS
[     6.089] (II) Loading extension XVideo
[     6.089] (II) Loading extension XVideo-MotionCompensation
[     6.089] (II) Loading extension X-Resource
[     6.089] (II) LoadModule: "dbe"
[     6.089] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     6.089] (II) Module dbe: vendor="X.Org Foundation"
[     6.089] 	compiled for 1.10.4, module version = 1.0.0
[     6.089] 	Module class: X.Org Server Extension
[     6.089] 	ABI class: X.Org Server Extension, version 5.0
[     6.089] (II) Loading extension DOUBLE-BUFFER
[     6.089] (II) LoadModule: "glx"
[     6.089] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     6.089] (II) Module glx: vendor="X.Org Foundation"
[     6.089] 	compiled for 1.10.4, module version = 1.0.0
[     6.089] 	ABI class: X.Org Server Extension, version 5.0
[     6.089] (==) AIGLX enabled
[     6.089] (II) Loading extension GLX
[     6.089] (II) LoadModule: "record"
[     6.090] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     6.090] (II) Module record: vendor="X.Org Foundation"
[     6.090] 	compiled for 1.10.4, module version = 1.13.0
[     6.090] 	Module class: X.Org Server Extension
[     6.090] 	ABI class: X.Org Server Extension, version 5.0
[     6.090] (II) Loading extension RECORD
[     6.090] (II) LoadModule: "dri"
[     6.090] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     6.090] (II) Module dri: vendor="X.Org Foundation"
[     6.090] 	compiled for 1.10.4, module version = 1.0.0
[     6.090] 	ABI class: X.Org Server Extension, version 5.0
[     6.090] (II) Loading extension XFree86-DRI
[     6.090] (II) LoadModule: "dri2"
[     6.090] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     6.090] (II) Module dri2: vendor="X.Org Foundation"
[     6.090] 	compiled for 1.10.4, module version = 1.2.0
[     6.090] 	ABI class: X.Org Server Extension, version 5.0
[     6.090] (II) Loading extension DRI2
[     6.090] (==) Matched intel as autoconfigured driver 0
[     6.090] (==) Matched vesa as autoconfigured driver 1
[     6.090] (==) Matched fbdev as autoconfigured driver 2
[     6.090] (==) Assigned the driver to the xf86ConfigLayout
[     6.090] (II) LoadModule: "intel"
[     6.090] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     6.090] (II) Module intel: vendor="X.Org Foundation"
[     6.090] 	compiled for 1.10.4, module version = 2.15.901
[     6.090] 	Module class: X.Org Video Driver
[     6.090] 	ABI class: X.Org Video Driver, version 10.0
[     6.090] (II) LoadModule: "vesa"
[     6.091] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.091] (II) Module vesa: vendor="X.Org Foundation"
[     6.091] 	compiled for 1.10.2, module version = 2.3.0
[     6.091] 	Module class: X.Org Video Driver
[     6.091] 	ABI class: X.Org Video Driver, version 10.0
[     6.091] (II) LoadModule: "fbdev"
[     6.091] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.091] (II) Module fbdev: vendor="X.Org Foundation"
[     6.091] 	compiled for 1.10.0, module version = 0.4.2
[     6.091] 	ABI class: X.Org Video Driver, version 10.0
[     6.091] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[     6.091] (II) VESA: driver for VESA chipsets: vesa
[     6.091] (II) FBDEV: driver for framebuffer: fbdev
[     6.091] (++) using VT number 7

[     6.092] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     6.092] (WW) Falling back to old probe method for vesa
[     6.092] (WW) Falling back to old probe method for fbdev
[     6.092] (II) Loading sub module "fbdevhw"
[     6.092] (II) LoadModule: "fbdevhw"
[     6.092] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.092] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.092] 	compiled for 1.10.4, module version = 0.0.2
[     6.092] 	ABI class: X.Org Video Driver, version 10.0
[     6.092] drmOpenDevice: node name is /dev/dri/card0
[     6.092] drmOpenDevice: open result is 9, (OK)
[     6.092] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[     6.092] drmOpenDevice: node name is /dev/dri/card0
[     6.092] drmOpenDevice: open result is 9, (OK)
[     6.092] drmOpenByBusid: drmOpenMinor returns 9
[     6.092] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[     6.092] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     6.092] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     6.092] (==) intel(0): RGB weight 888
[     6.092] (==) intel(0): Default visual is TrueColor
[     6.092] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT2)
[     6.092] (--) intel(0): Chipset: "Sandybridge Desktop (GT2)"
[     6.092] (**) intel(0): Relaxed fencing enabled
[     6.092] (**) intel(0): Wait on SwapBuffers? enabled
[     6.092] (**) intel(0): Triple buffering? enabled
[     6.092] (**) intel(0): Framebuffer tiled
[     6.092] (**) intel(0): Pixmaps tiled
[     6.092] (**) intel(0): 3D buffers tiled
[     6.092] (**) intel(0): SwapBuffers wait enabled
[     6.092] (==) intel(0): video overlay key set to 0x101fe
[     6.092] (II) intel(0): Output VGA1 has no monitor section
[     6.115] (II) intel(0): Output HDMI1 has no monitor section
[     6.164] (II) intel(0): Output DP1 has no monitor section
[     6.408] (II) intel(0): Output HDMI2 has no monitor section
[     6.456] (II) intel(0): Output DP2 has no monitor section
[     6.456] (II) intel(0): EDID for output VGA1
[     6.481] (II) intel(0): EDID for output HDMI1
[     6.528] (II) intel(0): EDID for output DP1
[     6.772] (II) intel(0): EDID for output HDMI2
[     6.772] (II) intel(0): Manufacturer: PIO  Model: 9e  Serial#: 16843009
[     6.772] (II) intel(0): Year: 2006  Week: 0
[     6.772] (II) intel(0): EDID Version: 1.3
[     6.772] (II) intel(0): Digital Display Input
[     6.772] (II) intel(0): Max Image Size [cm]: horiz.: 96  vert.: 54
[     6.772] (II) intel(0): Gamma: 2.20
[     6.772] (II) intel(0): DPMS capabilities: Off
[     6.772] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     6.772] (II) intel(0): First detailed timing is preferred mode
[     6.772] (II) intel(0): redX: 0.683 redY: 0.317   greenX: 0.313 greenY: 0.581
[     6.772] (II) intel(0): blueX: 0.139 blueY: 0.050   whiteX: 0.289 whiteY: 0.280
[     6.772] (II) intel(0): Manufacturer's mask: 0
[     6.772] (II) intel(0): Supported detailed timing:
[     6.772] (II) intel(0): clock: 74.2 MHz   Image Size:  952 x 536 mm
[     6.772] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     6.772] (II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[     6.772] (II) intel(0): Supported detailed timing:
[     6.772] (II) intel(0): clock: 27.0 MHz   Image Size:  952 x 536 mm
[     6.772] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[     6.772] (II) intel(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[     6.772] (II) intel(0): Ranges: V min: 59 V max: 61 Hz, H min: 15 H max: 46 kHz, PixClock max 85 MHz
[     6.772] (II) intel(0): Monitor name: PRO-xx40HD
[     6.772] (II) intel(0): Supported detailed timing:
[     6.772] (II) intel(0): clock: 74.2 MHz   Image Size:  952 x 536 mm
[     6.772] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[     6.772] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[     6.772] (II) intel(0): Supported detailed timing:
[     6.772] (II) intel(0): clock: 27.0 MHz   Image Size:  715 x 536 mm
[     6.772] (II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[     6.772] (II) intel(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[     6.772] (II) intel(0): Supported detailed timing:
[     6.772] (II) intel(0): clock: 27.0 MHz   Image Size:  952 x 536 mm
[     6.772] (II) intel(0): h_active: 1440  h_sync: 1478  h_sync_end 1602 h_blank_end 1716 h_border: 0
[     6.772] (II) intel(0): v_active: 240  v_sync: 244  v_sync_end 247 v_blanking: 262 v_border: 0
[     6.772] (II) intel(0): Supported detailed timing:
[     6.772] (II) intel(0): clock: 27.0 MHz   Image Size:  715 x 536 mm
[     6.772] (II) intel(0): h_active: 1440  h_sync: 1478  h_sync_end 1602 h_blank_end 1716 h_border: 0
[     6.772] (II) intel(0): v_active: 240  v_sync: 244  v_sync_end 247 v_blanking: 262 v_border: 0
[     6.772] (II) intel(0): Number of EDID sections to follow: 1
[     6.772] (II) intel(0): EDID (in hex):
[     6.772] (II) intel(0): 	00ffffffffffff00412f9e0001010101
[     6.772] (II) intel(0): 	00100103806036782ad7b3ae51509423
[     6.772] (II) intel(0): 	0c4a4700000001010101010101010101
[     6.772] (II) intel(0): 	010101010101011d8018711c1620582c
[     6.772] (II) intel(0): 	2500b8183200009e8c0ad08a20e02d10
[     6.772] (II) intel(0): 	103e9600b81832000018000000fd003b
[     6.772] (II) intel(0): 	3d0f2e08000a202020202020000000fc
[     6.772] (II) intel(0): 	0050524f2d7878343048440a20200135
[     6.772] (II) intel(0): 	02031c76488503040201070620230907
[     6.772] (II) intel(0): 	078301000066030c00100080011d0072
[     6.772] (II) intel(0): 	51d01e206e285500b8183200001e8c0a
[     6.772] (II) intel(0): 	d08a20e02d10103e9600cb1822000018
[     6.772] (II) intel(0): 	8c0aa01451f01600267c4300b8183200
[     6.772] (II) intel(0): 	00988c0aa01451f01600267c4300cb18
[     6.772] (II) intel(0): 	22000098000000000000000000000000
[     6.772] (II) intel(0): 	00000000000000000000000000000037
[     6.772] (II) intel(0): Printing probed modes for output HDMI2
[     6.772] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[     6.772] (II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[     6.820] (II) intel(0): EDID for output DP2
[     6.820] (II) intel(0): Output VGA1 disconnected
[     6.820] (II) intel(0): Output HDMI1 disconnected
[     6.820] (II) intel(0): Output DP1 disconnected
[     6.820] (II) intel(0): Output HDMI2 connected
[     6.820] (II) intel(0): Output DP2 disconnected
[     6.820] (II) intel(0): Using exact sizes for initial modes
[     6.820] (II) intel(0): Output HDMI2 using initial mode 1280x720
[     6.820] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     6.820] (II) intel(0): Kernel page flipping support detected, enabling
[     6.820] (==) intel(0): DPI set to (96, 96)
[     6.820] (II) Loading sub module "fb"
[     6.820] (II) LoadModule: "fb"
[     6.820] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.820] (II) Module fb: vendor="X.Org Foundation"
[     6.820] 	compiled for 1.10.4, module version = 1.0.0
[     6.820] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     6.820] (II) Loading sub module "dri2"
[     6.820] (II) LoadModule: "dri2"
[     6.820] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     6.820] (II) Module dri2: vendor="X.Org Foundation"
[     6.820] 	compiled for 1.10.4, module version = 1.2.0
[     6.820] 	ABI class: X.Org Server Extension, version 5.0
[     6.820] (II) UnloadModule: "vesa"
[     6.820] (II) Unloading vesa
[     6.820] (II) UnloadModule: "fbdev"
[     6.820] (II) Unloading fbdev
[     6.820] (II) UnloadModule: "fbdevhw"
[     6.820] (II) Unloading fbdevhw
[     6.820] (==) Depth 24 pixmap format is 32 bpp
[     6.820] (II) intel(0): [DRI2] Setup complete
[     6.820] (II) intel(0): [DRI2]   DRI driver: i965
[     6.820] (II) intel(0): Allocated new frame buffer 1280x720 stride 5120, tiled
[     6.821] (II) UXA(0): Driver registered support for the following operations:
[     6.821] (II)         solid
[     6.821] (II)         copy
[     6.821] (II)         composite (RENDER acceleration)
[     6.821] (II)         put_image
[     6.821] (II)         get_image
[     6.821] (==) intel(0): Backing store disabled
[     6.821] (==) intel(0): Silken mouse enabled
[     6.821] (II) intel(0): Initializing HW Cursor
[     6.880] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     6.880] (==) intel(0): DPMS enabled
[     6.880] (==) intel(0): Intel XvMC decoder enabled
[     6.880] (II) intel(0): Set up textured video
[     6.880] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[     6.880] (II) intel(0): direct rendering: DRI2 Enabled
[     6.880] (==) intel(0): hotplug detection: "enabled"
[     6.880] (--) RandR disabled
[     6.880] (II) Initializing built-in extension Generic Event Extension
[     6.880] (II) Initializing built-in extension SHAPE
[     6.880] (II) Initializing built-in extension MIT-SHM
[     6.880] (II) Initializing built-in extension XInputExtension
[     6.880] (II) Initializing built-in extension XTEST
[     6.880] (II) Initializing built-in extension BIG-REQUESTS
[     6.880] (II) Initializing built-in extension SYNC
[     6.880] (II) Initializing built-in extension XKEYBOARD
[     6.880] (II) Initializing built-in extension XC-MISC
[     6.880] (II) Initializing built-in extension SECURITY
[     6.880] (II) Initializing built-in extension XINERAMA
[     6.880] (II) Initializing built-in extension XFIXES
[     6.880] (II) Initializing built-in extension RENDER
[     6.880] (II) Initializing built-in extension RANDR
[     6.880] (II) Initializing built-in extension COMPOSITE
[     6.880] (II) Initializing built-in extension DAMAGE
[     6.880] (II) Initializing built-in extension GESTURE
[     6.883] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
[     6.885] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     6.885] (II) AIGLX: enabled GLX_INTEL_swap_event
[     6.885] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     6.885] (II) AIGLX: enabled GLX_SGI_make_current_read
[     6.885] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     6.885] (II) AIGLX: Loaded and initialized i965
[     6.885] (II) GLX: Initialized DRI2 GL provider for screen 0
[     6.885] (II) intel(0): Setting screen physical size to 338 x 190
[     6.889] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     6.893] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     6.893] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.893] (II) LoadModule: "evdev"
[     6.893] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.894] (II) Module evdev: vendor="X.Org Foundation"
[     6.894] 	compiled for 1.10.2, module version = 2.6.0
[     6.894] 	Module class: X.Org XInput Driver
[     6.894] 	ABI class: X.Org XInput driver, version 12.3
[     6.894] (II) Using input driver 'evdev' for 'Power Button'
[     6.894] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.894] (**) Power Button: always reports core events
[     6.894] (**) Power Button: Device: "/dev/input/event1"
[     6.894] (--) Power Button: Found keys
[     6.894] (II) Power Button: Configuring as keyboard
[     6.894] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     6.894] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     6.894] (**) Option "xkb_rules" "evdev"
[     6.894] (**) Option "xkb_model" "pc105"
[     6.894] (**) Option "xkb_layout" "us"
[     6.895] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     6.895] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.895] (II) Using input driver 'evdev' for 'Power Button'
[     6.895] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.895] (**) Power Button: always reports core events
[     6.895] (**) Power Button: Device: "/dev/input/event0"
[     6.895] (--) Power Button: Found keys
[     6.895] (II) Power Button: Configuring as keyboard
[     6.895] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     6.895] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[     6.895] (**) Option "xkb_rules" "evdev"
[     6.895] (**) Option "xkb_model" "pc105"
[     6.895] (**) Option "xkb_layout" "us"
[     6.897] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event5)
[     6.897] (II) No input driver/identifier specified (ignoring)
[     6.897] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event6)
[     6.897] (II) No input driver/identifier specified (ignoring)
[     6.898] (II) config/udev: Adding input device Dell Dell USB Keyboard Hub (/dev/input/event3)
[     6.898] (**) Dell Dell USB Keyboard Hub: Applying InputClass "evdev keyboard catchall"
[     6.898] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard Hub'
[     6.898] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.898] (**) Dell Dell USB Keyboard Hub: always reports core events
[     6.898] (**) Dell Dell USB Keyboard Hub: Device: "/dev/input/event3"
[     6.898] (--) Dell Dell USB Keyboard Hub: Found keys
[     6.898] (II) Dell Dell USB Keyboard Hub: Configuring as keyboard
[     6.898] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.0/input/input3/event3"
[     6.898] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard Hub" (type: KEYBOARD)
[     6.898] (**) Option "xkb_rules" "evdev"
[     6.898] (**) Option "xkb_model" "pc105"
[     6.898] (**) Option "xkb_layout" "us"
[     6.898] (II) config/udev: Adding input device Dell Dell USB Keyboard Hub (/dev/input/event4)
[     6.898] (**) Dell Dell USB Keyboard Hub: Applying InputClass "evdev keyboard catchall"
[     6.898] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard Hub'
[     6.898] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.898] (**) Dell Dell USB Keyboard Hub: always reports core events
[     6.898] (**) Dell Dell USB Keyboard Hub: Device: "/dev/input/event4"
[     6.898] (--) Dell Dell USB Keyboard Hub: Found absolute axes
[     6.898] (II) evdev-grail: failed to open grail, no gesture support
[     6.898] (--) Dell Dell USB Keyboard Hub: Found keys
[     6.898] (II) Dell Dell USB Keyboard Hub: Configuring as mouse
[     6.898] (II) Dell Dell USB Keyboard Hub: Configuring as keyboard
[     6.898] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1.1/2-1.1.1:1.1/input/input4/event4"
[     6.898] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard Hub" (type: KEYBOARD)
[     6.898] (**) Option "xkb_rules" "evdev"
[     6.898] (**) Option "xkb_model" "pc105"
[     6.898] (**) Option "xkb_layout" "us"
[     6.898] (II) Dell Dell USB Keyboard Hub: initialized for absolute axes.
[     6.898] (**) Dell Dell USB Keyboard Hub: (accel) keeping acceleration scheme 1
[     6.898] (**) Dell Dell USB Keyboard Hub: (accel) acceleration profile 0
[     6.899] (**) Dell Dell USB Keyboard Hub: (accel) acceleration factor: 2.000
[     6.899] (**) Dell Dell USB Keyboard Hub: (accel) acceleration threshold: 4
[     6.899] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event2)
[     6.899] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[     6.899] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[     6.899] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.899] (**) USB Optical Mouse: always reports core events
[     6.899] (**) USB Optical Mouse: Device: "/dev/input/event2"
[     6.899] (--) USB Optical Mouse: Found 3 mouse buttons
[     6.899] (--) USB Optical Mouse: Found scroll wheel(s)
[     6.899] (--) USB Optical Mouse: Found relative axes
[     6.899] (--) USB Optical Mouse: Found x and y relative axes
[     6.899] (II) USB Optical Mouse: Configuring as mouse
[     6.899] (II) USB Optical Mouse: Adding scrollwheel support
[     6.899] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[     6.899] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.899] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input2/event2"
[     6.899] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[     6.899] (II) USB Optical Mouse: initialized for relative axes.
[     6.899] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[     6.899] (**) USB Optical Mouse: (accel) acceleration profile 0
[     6.899] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[     6.899] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[     6.899] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[     6.899] (II) No input driver/identifier specified (ignoring)
[     7.355] (II) intel(0): EDID vendor "PIO", prod id 158
[     7.355] (II) intel(0): Using EDID range info for horizontal sync
[     7.355] (II) intel(0): Using EDID range info for vertical refresh
[     7.355] (II) intel(0): Printing DDC gathered Modelines:
[     7.355] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[     7.355] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[     7.355] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[     7.355] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[     7.356] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[     7.356] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[     7.715] (II) intel(0): EDID vendor "PIO", prod id 158
[     7.715] (II) intel(0): Using hsync ranges from config file
[     7.715] (II) intel(0): Using vrefresh ranges from config file
[     7.715] (II) intel(0): Printing DDC gathered Modelines:
[     7.715] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[     7.715] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[     7.715] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[     7.715] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[     7.715] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[     7.715] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[     8.103] (II) intel(0): EDID vendor "PIO", prod id 158
[     8.104] (II) intel(0): Using hsync ranges from config file
[     8.104] (II) intel(0): Using vrefresh ranges from config file
[     8.104] (II) intel(0): Printing DDC gathered Modelines:
[     8.104] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[     8.104] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[     8.104] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[     8.104] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[     8.104] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[     8.104] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[     8.720] (II) intel(0): EDID vendor "PIO", prod id 158
[     8.720] (II) intel(0): Using hsync ranges from config file
[     8.720] (II) intel(0): Using vrefresh ranges from config file
[     8.720] (II) intel(0): Printing DDC gathered Modelines:
[     8.720] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[     8.720] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[     8.720] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[     8.720] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[     8.720] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[     8.720] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)
[     9.080] (II) intel(0): EDID vendor "PIO", prod id 158
[     9.080] (II) intel(0): Using hsync ranges from config file
[     9.080] (II) intel(0): Using vrefresh ranges from config file
[     9.080] (II) intel(0): Printing DDC gathered Modelines:
[     9.080] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[     9.080] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[     9.080] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[     9.080] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[     9.080] (II) intel(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[     9.080] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz)

```

I also ran the 

export DISPLAY=:0

and

xrandr -s 720x480

The TV screen went blank and it looks like the ssh is stuck now. Its been 10 mins and the terminal has not responded to the command. Any sugestions? Should I restart the box? Thanks

**UPDATE
it came back with: Write failed: Broken pipe

The box was completely unresponsive and i could not ssh into it, get to the web interface or ping it. I shut down the box for now.

---

### Post by drewdin on 2012-04-16
Anyone have any suggestions? Thanks

---

### Post by drewdin on 2012-04-17
selfless attempt to bump the thread for help :)

---

### Post by nickrout on 2012-04-17
I have no idea what is wrong. Try approaching the intel forums, I see some references to this motherboard in there. Google will have told you that already.

---

### Post by drewdin on 2012-04-18
thanks, ill try intel forums

---


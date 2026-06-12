---
title: "Direct Rendering module (drm) will not load (Cannot allocate memory)"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by kalibyrn on 2007-02-04
Hello...  I'm using the fglrx video driver with an ATI Radeon 9800 Pro, and everything was working great!  I had beryl working, and it was absolulely beautiful.  Then one day, for no apparent reason, when I turned the computer on beryl wouldn't work.  Firefox was excruciatingly slow.  I've tried the ati, radeon, and fglrx drivers, but to no avail.  (I could have switched improperly, however...)  If I can't get beryl working again, that's fine, although not ideal.  But I at least want to get back to the performance level I had BEFORE I moved to beryl.  As it stands right now, I have to write this message in vi and paste it into Firefox for it to be bearable.

I'm running Ubuntu 6.10.

dmesg shows that fglrx is loading..  However there is kernel AGP support already, and I'm not sure if that's good or bad.

```
[fglrx] Internal AGP support requested, but kernel AGP support active.
[fglrx] Have to use kernel AGP support to avoid conflicts.
[fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[fglrx] total      GART = 67108864
[fglrx] free       GART = 51113984
[fglrx] max single GART = 51113984
[fglrx] total      LFB  = 134217728
[fglrx] free       LFB  = 108974080
[fglrx] max single LFB  = 108974080
[fglrx] total      Inv  = 0
[fglrx] free       Inv  = 0
[fglrx] max single Inv  = 0
[fglrx] total      TIM  = 0
```

Anyway, I thought I had narrowed it down to this -- drm will not load.

```
rob@parnassus:/var/log$ lsmod | grep drm
rob@parnassus:/var/log$ sudo modprobe drm
FATAL: Error inserting drm (/lib/modules/2.6.17-10-generic/kernel/drivers/char/drm/drm.ko): Cannot allocate memory
rob@parnassus:/var/log$ 
```

The confusing thing is that in Xorg.0.log, it says it IS loading...  Maybe it's already in userspace, and therefore the kernel module can't load?  

```
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7330000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.33.6
(II) fglrx(0):     Date: Jan  8 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.17-10-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [pci] find AGP GART
(II) fglrx(0): [agp] Mode=0x1f004a1b bridge: 0x8086/0x2570
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f004b1a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xf8000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f004312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xe8000000 FBMappedSize: 0x00954000
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,1528)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1600 x 328
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		24 128x128 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(**) fglrx(0): Video overlay enabled on CRTC1
(II) fglrx(0): Interrupt handler installed at IRQ 177.
(II) fglrx(0): Exposed events to the /proc interface
```

So I ran fglrxinfo, and this is what I get:

```
rob@parnassus:/var/log$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

And glxinfo shows this...  

```
rob@parnassus:/var/log$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.2 (2.0.6286 (8.33.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon

```

Notice direct rendering is "No"...  I have no idea why.  I've noticed that the displays don't seem to match up.  fglrxinfo shows display :0.0, and glxinfo shows display :1.0.  So I thought I'd take a peak in xorg.conf, and that appears to be ok...  Here are the pertinent sections:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
    BusID       "PCI:1:0:0"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

Maybe it has to do with the fact I have two monitors.  They both display the same thing right now -- I haven't bothered to tackle Xinerama or any other sort of double-monitor set up yet.

Anyway, I've followed a variety of howtos, and to no avail.  By what I gather, direct rendering SHOULD be working.  

Any help would be greatly appreciated...

---

### Post by kalibyrn on 2007-02-04
It DID have something to do with dual monitors!!  I guess not all of the "components" could agree on what display to use.  Somehow, I got the performance I had before I installed beryl back.  It was all in the xorg.conf file.  The "Cannot allocate memory" error in the subject must have been a red herring.

Here is the new xorg.conf file.

```
Section "ServerLayout"
	Identifier     "Default Layout"
    Screen      0  "ScreenLeft" 0 0
    Screen      1  "ScreenRight" 1600 176
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
    #Option      "Xinerama" "true"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "MonitorRight"
	VendorName   "Daytek"
	ModelName    "Vista V72"
	HorizSync    20.0 - 87.0
	VertRefresh  40.0 - 160.0
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "MonitorLeft"
	VendorName   "Dell"
	ModelName    "P1110"
	HorizSync    30.0 - 121.0
	VertRefresh  48.0 - 160.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
    Identifier  "ATI Radeon 9800 Pro Primary"
	Driver      "fglrx"
    BusID       "PCI:1:0:0"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
    Screen      0
EndSection

Section "Device"
    Identifier  "ATI Radeon 9800 Pro Secondary"
	Driver      "fglrx"
    BusID       "PCI:1:0:0"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
    Screen      1
EndSection

Section "Screen"
    Identifier  "ScreenLeft"
    Device      "ATI Radeon 9800 Pro Primary"
    Monitor     "MonitorLeft"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1600x1200" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
    Identifier  "ScreenRight"
    Device      "ATI Radeon 9800 Pro Secondary"
    Monitor     "MonitorRight"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

I renamed a lot of the Identifiers (kind of anal that way) but the major changes are still evident.  Here are a few things that helped:

[LIST=1]
[*]I created another "Device" entry for my card, with a different "Screen" value.
[*]In ServerLayout, I list both screens.
[*]Note that I enabled and then disabled Xinerama.  Xinerama seems to block DRI...?
[/LIST]

The output of glxinfo and fglrxinfo appear to agree a little more now...

```
rob@parnassus:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6286 (8.33.6)

display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

```
rob@parnassus:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
...<snip>...
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6286 (8.33.6)

...<snip>...

display: :0  screen: 1
direct rendering: Yes
...<snip>...
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

Now I have two screens, which are somewhat disconnected.  It appears I can launch an app in one window, and it will remain in that window no matter what.  That's ok -- I can live with that for now.  I'm at least back in business to some degree.  Now I gotta get beryl working again...  ;)

By the way, I'm currently using the Gnome window manager again, instead of XGL, which I was using with beryl.  I will try again with XGL and see what happens.

---


---
title: "ATI flgrx + glx problem (no direct rendering)"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by linumik on 2006-09-22
I installed fglrx drivers version 8.25.18. The /var/log/Xorg.0.log file shows that direct rendering is enabled. However, glxinfo says that it's disabled. Any suggestions?

```

(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1408 x 373
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): Interrupt handler installed at IRQ 169.
(==) RandR enabled

```

```

> glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias

```

```

> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

```

> ls -la /usr/lib/libGL.*
lrwxrwxrwx 1 root root 27 2006-09-21 18:19 /usr/lib/libGL.so -> /usr/lib/fglrx/libGL.so.1.2
lrwxrwxrwx 1 root root 27 2006-09-21 18:19 /usr/lib/libGL.so.1 -> /usr/lib/fglrx/libGL.so.1.2

```

---

### Post by ashrack on 2006-09-22
do the following in the terminal:
```
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```
then reboot the computer and post if it works then

---

### Post by Ferrat on 2006-09-22
Did you really use create new module installation and not the preset once that are on the graficinterfaced installation? Did you recomplie the kernel?

---

### Post by linumik on 2006-09-22
I had that already done
```

> ls -la /usr/lib/xorg/modules/dri
lrwxrwxrwx 1 root root 12 2006-09-21 13:26 /usr/lib/xorg/modules/dri -> /usr/lib/dri

```

That doesn't help.

---

### Post by linumik on 2006-09-22
> **Ferrat said:**
> Did you really use create new module installation and not the preset once that are on the graficinterfaced installation? Did you recomplie the kernel?

I tried to install with apt-get and with ATI graphical installer - same result. I didn't recompile the kernel. The fglrx module loads fine and Xorg.log file shows that direct rendering is on. GLX doesn't want to use it though.

---

### Post by ashrack on 2006-09-22
well I had similar problems. And this is what I did to fixed them:
I removed everything relating to FGLRX and then also did:
```
rm -rf /usr/lib/dri /usr/lib/xorg/modules/dri
```
afterwards restarted the computer and reinstalled the drivers like this guide says:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

and afterwards it started to work.
ps. I tried this method lots of times by now when I was installing newer drivers for FGLRX in a hope they would fix a bug that is 2years old by now, and the method always worked.

---

### Post by linumik on 2006-09-22
Ok. Found solution. It has nothing to do with reinstalling anything as it was almost working already (the driver) and only GLX was confused.

so apparently, running this 'LIBGL_DEBUG=verbose fglrxinfo' provides all information one needs:
```

> LIBGL_DEBUG=verbose fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.25.18 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/lib/modules/dri/fglrx_dri.so failed (/usr/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.25.18 fglrx (screen 1)
libGL: OpenDriver: trying /usr/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/lib/modules/dri/fglrx_dri.so failed (/usr/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.25.18 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/lib/modules/dri/fglrx_dri.so failed (/usr/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.25.18 fglrx (screen 1)
libGL: OpenDriver: trying /usr/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/lib/modules/dri/fglrx_dri.so failed (/usr/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: fglrx_dri.so
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Then it's obvious how to fix it:
```

sudo ln -s /usr/lib/xorg/modules/ /usr/lib/modules

```

No reboots or reinstalls.

---

### Post by baytuni on 2006-11-29
mine is```
 LIBGL_DEBUG=verbose fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```
so what is my problem??

---

### Post by linumik on 2006-11-29
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

```

That's your problem. Check xorg.conf file and make sure you have in the Section "Module"

```

    Load  "glx"
    Load  "dri"
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

```

And also have this section
```

Section "DRI"
    Mode 0666
EndSection

```

---

### Post by baytuni on 2006-11-29
so I have a new error. 
```
 LIBGL_DEBUG=verbose fglrxinfo
libGL error: XF86DRIQueryDirectRenderingCapable returned false
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1
```

I also have some problem while installing latest fglrx from [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](wiki) page in this thread [http://ubuntuforums.org/showthread.php?p=1822940#post1822940](this)

---

### Post by linumik on 2006-11-29
Post your xorg.conf file. The problem is there.

---

### Post by baytuni on 2006-11-29
Here you are
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
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
	SubSection "extmod"
		Option	    "omit xfree86-dga"   # don't initialise the DGA extension
	EndSubSection
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "tr"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "LG LSS"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI RADEON X550"
	Driver      "ati"
	Option	    "XaaNoOffscreenPixmaps" "true"
	BusID       "PCI:4:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection



Section "Screen"
	Identifier "Default Screen"
	Device     "ATI RADEON X550"
	Monitor    "LG LSS"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


```

---

### Post by kesman on 2006-11-29
Your conf-file is quite messed up :P
Seems like you are having both ati and fglrx-modules listed there.
Try commenting out (adding # in front of a line) the whole device section with ati as driver. Then reboot and try again.

---

### Post by kesman on 2006-11-29
Like this:
```

#Section "Device"
#	Identifier  "ATI RADEON X550"
#	Driver      "ati"
#	Option	    "XaaNoOffscreenPixmaps" "true"
#	BusID       "PCI:4:0:0"
#EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection


```

Oh and change the Identifier to ATI RADEON X550 instead of that aticonfig-monster :P

---

### Post by kesman on 2006-11-29
Oh man, you even have multiple screen sections.. I'm not sure how it affects if you have many, but I think you should remove all but that which has'n been produced by aticonfig.

---

### Post by baytuni on 2006-11-29
Ok I got it. I erased all the duplicate sections and conflictions 
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
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
	SubSection "extmod"
		Option	    "omit xfree86-dga"   # don't initialise the DGA extension
	EndSubSection
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "tr"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
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
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```
but I still have 

```
 LIBGL_DEBUG=verbose fglrxinfo
libGL error: XF86DRIQueryDirectRenderingCapable returned false
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

and 
```
$ sudo depmod -a

WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/agpgart.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/ali-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/amd-k7-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/amd64-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/ati-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/efficeon-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/agp/intel-agp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/synclink.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/synclink_gt.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/synclinkmp.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/tipar.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/tlclk.ko is not an elf object
WARNING: Module /lib/modules/2.6.17-10-generic/kernel/drivers/char/toshiba.ko is not an elf object
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/mouse/psmouse.ko: File too large
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/mouse/sermouse.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/mouse/vsxxxaa.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/serio/ct82c710.ko: No such device
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/serio/parkbd.ko: No such device
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/serio/pcips2.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/serio/serio_raw.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/serio/serport.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/touchscreen/ads7846.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/touchscreen/elo.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/touchscreen/gunze.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/touchscreen/mk712.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/input/touchscreen/mtouch.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/aacraid/aacraid.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/lpfc/lpfc.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/sas/sas_class.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/sd_mod.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/sg.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/sim710.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/sr_mod.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/st.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/sym53c416.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/t128.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/tmscsim.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/u14-34f.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/ultrastor.ko: Input/output error
WARNING: Can't read module /lib/modules/2.6.17-10-generic/kernel/drivers/scsi/wd7000.ko: Input/output error

```

---

### Post by Blario on 2006-11-30
> **linumik said:**
> ```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

```

That's your problem. Check xorg.conf file and make sure you have in the Section "Module"

```

    Load  "glx"
    Load  "dri"
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

```

And also have this section
```

Section "DRI"
    Mode 0666
EndSection

```

I have those statements in my xorg.conf file, and I have the exact same output from that file.

---

### Post by linumik on 2006-11-30
your original config file looked just fine and should work, the only thing that is missing is extended parameters in the section with fglrx driver.

here is mine:
```

    Driver      "fglrx"

    BusID       "PCI:1:0:0"
    Screen      0

    # === disable PnP Monitor  ===
    #Option                              "NoDDC"

    # === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no" 
        
    # === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr

    # ### FireGL DDX driver module specific settings ###
    # === Screen Management ===
    Option "DesktopSetup"      "0x00000100"
    Option "ScreenOverlap"     "0" 

    Option "DPMS"              "off"
    
    # === TV-out Management ===
    Option "TVFormat"                   "NTSC-M"     
    Option "TVStandard"                 "VIDEO"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
    
    # === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"

    # === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"

    # === OpenGL Overlay ===
    # Note: When OpenGL Overlay is enabled, Video Overlay
    #       will be disabled automatically
    Option "OpenGLOverlay"              "off"
    
    # === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
    
    # === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
    
    # === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
    
    # === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
    
    # === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no" 

```

you obviously need a correct BusID, you can find it out from lspci.
for example:
```

> lspci
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]

```

Also, if it still doesn't work for you, post also the /var/log/Xorg.0.log file

---

### Post by Blario on 2006-11-30
> **linumik said:**
> # ### FireGL DDX driver module specific settings ###
    # === Screen Management ===
    Option "DesktopSetup"      "0x00000100"
    Option "ScreenOverlap"     "0" 

Are the Firegl DDX driver settings in your config supposed to be in everyone's file, or is that specific to you?

---

### Post by linumik on 2006-11-30
I guess, those particular won't be needed, but then again, fglrx will ignore them if they are not used. Xorg.0.log file would tell you for sure. So, I'd say, it is safe to have those in any fglrx config file.

---

### Post by Blario on 2006-11-30
> **linumik said:**
> I guess, those particular won't be needed, but then again, fglrx will ignore them if they are not used. Xorg.0.log file would tell you for sure. So, I'd say, it is safe to have those in any fglrx config file.

Alright, here's my issue.  I have been at this for two days now, and it almost seems like I've read everything there is to read as far as common problems with this thing.  Yet I get an error that no one else seems to get.  

For everyone else, once they add the disable composite lines to xorg.conf, their DRI start working.  Everytime I do that, my comp hard crashes upon boot.  I understand that disable composite is necessary for DRI with the fglrx driver, but I can't seem to get around this issue.  I will post my xorg log file for others to reference and hopefully provide some insight.

---

### Post by Blario on 2006-11-30
```

(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(II) fglrx(0):  SAMSUNG
(II) fglrx(0):  LTN154X3-L01
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 301/250MHz @ 60Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 13 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   68.94  1280 1296 1344 1408  800 801 804 816
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.0
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.0
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xb0100000 - 0xb010ffff (0x10000) MX[B]
        [1] 0   0       0xc0000000 - 0xcfffffff (0x10000000) MX[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xb020a400 - 0xb020a4ff (0x100) MX[B]
        [7] -1  0       0xb0208800 - 0xb02088ff (0x100) MX[B]
        [8] -1  0       0xb0208c00 - 0xb0208cff (0x100) MX[B]
        [9] -1  0       0xb020a000 - 0xb020a0ff (0x100) MX[B]
        [10] -1 0       0xb0206000 - 0xb0207fff (0x2000) MX[B]
        [11] -1 0       0xb0204000 - 0xb0205fff (0x2000) MX[B]
        [12] -1 0       0xb0200000 - 0xb0203fff (0x4000) MX[B]
        [13] -1 0       0xb0208000 - 0xb02087ff (0x800) MX[B]
        [14] -1 0       0xb0003800 - 0xb00038ff (0x100) MX[B]
        [15] -1 0       0xb0003400 - 0xb00034ff (0x100) MX[B]
        [16] -1 0       0xb0003000 - 0xb00033ff (0x400) MX[B]
        [17] -1 0       0xb0002000 - 0xb0002fff (0x1000) MX[B]
        [18] -1 0       0xb0001000 - 0xb0001fff (0x1000) MX[B]
        [19] -1 0       0xb0000000 - 0xb0000fff (0x1000) MX[B]
        [20] -1 0       0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
        [21] -1 0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [22] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
        [23] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
        [24] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
        [25] 0  0       0x00009000 - 0x000090ff (0x100) IX[B]
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [27] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [28] -1 0       0x0000a000 - 0x0000a0ff (0x100) IX[B]
        [29] -1 0       0x00008410 - 0x0000841f (0x10) IX[B]
        [30] -1 0       0x00000374 - 0x00000374 (0x1) IX[B]
        [31] -1 0       0x00000170 - 0x00000170 (0x1) IX[B]
        [32] -1 0       0x000003f4 - 0x000003f4 (0x1) IX[B]
        [33] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [34] -1 0       0x00008400 - 0x0000840f (0x10) IX[B]
        [35] -1 0       0x00009000 - 0x000090ff (0x100) IX[B](B)
        [36] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [37] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): UMM Bus area: 0xc05e9000 (size=0x079f7000)
(II) fglrx(0): UMM area:     0x605e9000 (size=0x079f7000)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb6e9c000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.31.5
(II) fglrx(0):     Date: Nov  9 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.17-10-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [pcie] 131072 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x60000000 FBMappedSize: 0x005e9000
(II) fglrx(0): Splitting WC range: base: 0xc0000000, size: 0x5e9000
(II) fglrx(0): Splitting WC range: base: 0xc0400000, size: 0x1e9000
(II) fglrx(0): Splitting WC range: base: 0xc0500000, size: 0xe9000
(II) fglrx(0): Splitting WC range: base: 0xc0580000, size: 0x69000
(II) fglrx(0): Splitting WC range: base: 0xc05c0000, size: 0x29000
(II) fglrx(0): Splitting WC range: base: 0xc05e0000, size: 0x9000
(==) fglrx(0): Write-combining range (0xc05e8000,0x1000)
(==) fglrx(0): Write-combining range (0xc05e0000,0x9000)
(==) fglrx(0): Write-combining range (0xc05c0000,0x29000)
(==) fglrx(0): Write-combining range (0xc0580000,0x69000)
(==) fglrx(0): Write-combining range (0xc0500000,0xe9000)
(==) fglrx(0): Write-combining range (0xc0400000,0x1e9000)
(==) fglrx(0): Write-combining range (0xc0000000,0x5e9000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1210)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "UseFBDev" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete

```

To help summarize, I have the disable composite statement in my xorg.conf file.  DRI attempts to log, and as you can see, the log stops abruptly right there.  The comp hard crashes right there, and I have to comment out the disable composite statements in order to get X to start. Does anyone know what may be causing this and how to fix it? 

I notice I get a warning in there, "(WW) fglrx(0): Option "UseFBDev" is not used".  Is this a problem?

---

### Post by Blario on 2006-11-30
[http://gentoo-wiki.com/HOWTO_ATI_Drivers#DRI_problems_with_ATI_XPRESS_200M_PCIe](http://gentoo-wiki.com/HOWTO_ATI_Drivers#DRI_problems_with_ATI_XPRESS_200M_PCIe)

That describes my situation exactly, specific to the GPU & make&model of the comp.  I'm looking more into it.

---


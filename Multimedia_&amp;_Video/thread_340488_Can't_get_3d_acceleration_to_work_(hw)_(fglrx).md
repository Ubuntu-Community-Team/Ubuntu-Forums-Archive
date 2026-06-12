---
title: "Can't get 3d acceleration to work (hw) (fglrx)"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by zzarr on 2007-01-17
Hello!


This is what I got:

K8T800 MSI mainboard
AMD Athlon 64 3200+ (2200 MHz)
2 Gb RAM
ATI Radeon X800 XT Platinum Edition
250 Gb SATA disk + 250 Gb PATA (IDE) disk + 3 x 250 Gb USB 2.0 disks


This is what I run:
Linux version 2.6.15-27-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Fri Dec 8 18:00:07 UTC 2006
fglrx 8.28.8 (with kernel module)


This modules are loaded:

Module                  Size  Used by
fglrx                 402796  0
usb_storage            79648  3
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
ipv6                  286976  22
ppdev                   9668  0
powernow_k8            14304  0
cpufreq_powersave       1920  0
cpufreq_stats           6688  0
cpufreq_userspace       6496  1
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
freq_table              4928  2 powernow_k8,cpufreq_stats
tc1100_wmi              6884  0
video                  16324  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
container               4608  0
button                  6704  0
pcc_acpi               12416  0
sony_acpi               5580  0
ac                      5220  1 acpi_sbs
dev_acpi               11236  0
hotkey                 11492  0
xfs                   649696  4
exportfs                6528  1 xfs
af_packet              24520  2
dm_mod                 63256  1
md_mod                 76052  0
lp                     12356  0
tsdev                   8032  0
snd_seq_dummy           3908  0
snd_seq_oss            37216  0
snd_seq_midi            9600  0
snd_seq_midi_event      7520  2 snd_seq_oss,snd_seq_midi
snd_seq                58160  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
r1000                  17984  0
serio_raw               7748  0
floppy                 64676  0
pcspkr                  2244  0
psmouse                40004  0
i2c_viapro              9108  0
i2c_core               22848  2 i2c_acpi_ec,i2c_viapro
hci_usb                18004  2
parport_pc             37988  1
parport                39400  3 ppdev,lp,parport_pc
snd_via82xx            31128  1
gameport               16776  1 snd_via82xx
snd_ac97_codec        100224  1 snd_via82xx
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  2 snd_seq,snd_pcm
snd_page_alloc         11304  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8640  1 snd_via82xx
snd_rawmidi            26848  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    60004  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10784  1 snd
bluetooth              54212  7 rfcomm,l2cap,hci_usb
r8169                  31336  0
amd64_agp              13060  1
agpgart                36784  2 fglrx,amd64_agp
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
sg                     40160  0
evdev                  10176  1
reiserfs              284016  4
ide_generic             1504  0
ehci_hcd               36104  0
uhci_hcd               35536  0
usbcore               139172  5 usb_storage,hci_usb,ehci_hcd,uhci_hcd
ide_cd                 35780  0
cdrom                  41408  1 ide_cd
ide_disk               19136  2
generic                 5124  0
via82cxxx               9796  0 [permanent]
sd_mod                 20448  12
sata_via               10340  10
libata                 83440  1 sata_via
scsi_mod              145960  4 usb_storage,sg,sd_mod,libata
thermal                13768  0
processor              26888  2 powernow_k8,thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit


This is the problem I got:

(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


This is the result:

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
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
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

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None


This is what I feel:

Frustrated

Please help me, whats wrong?

Greetings Zzarr

---

### Post by crispy_420 on 2007-01-19
How about posting your xorg?

---

### Post by RudolfMDLT on 2007-01-19
Zzar,

Hi there,

Basics:

Please post

1) the output of fglrxinfo

2) glxgears -fps

3) sudo gedit /etc/X11/xorg.conf


If you wish - Please follow my HowTo from start to finnish and you should be fine!

[http://ubuntuforums.org/showthread.php?t=195845](http://ubuntuforums.org/showthread.php?t=195845)


I know you must be frustrated! Trust me, all ATI users have ben there! :)

Goodluck,

Cheers,

Rudolf

---

### Post by Extrapolation on 2007-01-19
I'd like to get in on this action too.

I have a Radeon 9200, which was always plenty fast in Windows, so something has to be wrong.  I followed [**this tutorial**]("http://ubuntuforums.org/showthread.php?t=305665&highlight=ati+amd") and it worked until I had to restart X, but then I could only boot Ubuntu in recovery mode.  I eventually apt-get removed Xorg (from the command line) and reinstalled it, and got back to the desktop, but of course I have no 3d acceleration, and the writer of the HowTo I followed has apparently vanished from the earth.

If you'll stick around and walk me (and Zzarr) through this, I'd be really grateful.  So far, no one has really taken the time.  Just let me know what I need to do to help you...help me.

---

### Post by crispy_420 on 2007-01-19
I saw that guide and it looks more complicated than it needs to be. Just go to ATI's website and go through the download section to get the driver installer. [HERE]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") is a direct link to it.

Install as directed in their guide. I don't remember if it auto changes your xorg or not. But you can always check it (/etc/X11/xorg.conf).

If you want I can post the section my xorg if you like. Just ask. Or if you're not sure on how to edit it or manage to screw up, just ask me. I've screwed mine up so many times that I think I can solve most issues.

Good luck.

---

### Post by Extrapolation on 2007-01-19
Following ANY method of the 10 I've tested so far, I reboot and end up at a blank screen where my monitor has no input.  Every time, I have to remove and re-install the Xorg driver, then restart GDM, to get back to anything but the recovery prompt.  This is driving me crazy!

Can anyone maybe tell me a step I'm likely missing, or something?  I follow all the tutorials step-by-step.

---

### Post by Extrapolation on 2007-01-20
OK, I installed ATI's drivers, as well as following a really elaborate tutorial that had me recompile my kernel.  All said and done, and I have the same framerates I had before.  At least I can get to my desktop now.

glxinfo produces the following:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x26 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x29 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x2a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2d  8 pc  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  1 0 None
0x2e  8 gs  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  1 0 None

```

Here's my xorg.conf

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
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
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
	Identifier   "L70S"
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
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor    "L70S"
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

glxgears -fps produces the following:

```
Warrning: unknown parameter: -fps
```

Can someone please tell me what to do?  I have wasted three miserable days on following every HowTo I can find, and I'm about to just throw my hands up and go back to Windows entirely!

---

### Post by crispy_420 on 2007-01-21
You don't need to include "-fps". My frames per secord show up after 5 seconds. I usually have atleast 4000-6000.

But if I remember correctly there is a better test for ATI cards:

> fgl_glxgears

This will get me around 700-860.

Here is my xorg:

> 
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
#Section "InputDevice"
#	Identifier  "Configured Mouse"
#	Driver      "mouse"
#	Option	    "CorePointer"
#	Option	    "Device" "/dev/input/mice"
#	Option	    "Protocol" "ExplorerPS/2"
#	Option	    "ZAxisMapping" "4 5"
#	Option	    "Emulate3Buttons" "true"
#EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/event5" #this should be that underlined name from 19-local.rules
	Option        "Buttons"        "10"
    	Option        "ZAxisMapping"        "4 5"
EndSection

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
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
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

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
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
	Identifier   "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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


And by the way, you left windows for a reason. If you go back, you'll see nothing has changed on the Microsoft front. Don't get me wrong, I don't dislike windows, just certain aspects of it.

---

### Post by Extrapolation on 2007-01-22
Thanks for posting your xorg.conf.  I replaced everything that was different in mine (that was relevant, but I still have the same problems.

Also, typing fgl_glxgears gives me this:
```

Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32

```

Again, thank you for your help, but I feel like some larger problem is hindering my system here.

---

### Post by crispy_420 on 2007-01-23
Just an idea but there a program (gui) to configure ATI cards for linux. I personally have not tried it yet, but it is called [fglrxconf]("http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/").

At this point it looks as though you have nothing left to miss. And if it screws you up you can always run *_sudo dpkg-reconfigure xserver-xorg_* to reconfigure from scratch.

---

### Post by Extrapolation on 2007-01-23
Just to let you know, I tried fglrxconf and it fixed nothing, so I ended up wiping all the relevant stuff and starting from scratch, with no Xorg driver at all, and following the tutorial from the wiki.  Lo and behold, it worked!  I have 3D acceleration now!  :guitar: 

Anyway, thanks for all your help, and your useful suggestions.  I actually did learn a lot from trying to fix this, so I guess "all's well that ends well," right?

---

### Post by blankSWFC on 2007-01-23
I think it was because in the xorg.conf file you posted before, you had several references to the "ati" driver, and not the fglrx driver.  Even tho the fglrx module was being loaded, the Xserver was still using the "ati" driver.

**Glad ya sorted it out tho :D !**


---

Also, from the looks of it you also used that dreadful aticonfig tool which it says to use after you install the official driver package from the ATI site.  In my experienced it has always failed to configure it correctly.

---


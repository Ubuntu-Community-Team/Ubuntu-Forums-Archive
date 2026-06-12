---
title: "Please help me get 3D acceleration working! (yet another ATi issue)"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by Martin A on 2006-08-20
Hi!
Despite making numerous posts on numerous forums, I still have no 3D acceleration. I'm using an ATi Radeon 9250, and I have tried the following howto pages:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910) (and I've been through that entire thread and tried ALL the suggestions there) 

I've yet to hear from a single person who has got this card working with the fglrx driver and after 2-3 weeks of trying I'm etting ready to give up and go back to Windows :( .

Here's the deal: with "fglrx" selected in xorg.conf, glxinfo gives me:

```
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
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
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

```

With "radeon" in xorg.conf I get much the same thing.

fglrxinfo returns the following:

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Any ideas or suggestions are greatly appreciated,

Martin

---

### Post by RichJacot on 2006-08-20
I'm not sure how your card compares to mine (ATI 9800 Pro).  I also had many many issues getting mine working.  I found this link and it finally worked, I repeat, finally.  From first glance this link may work for your card also.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Rich

---

### Post by Martin A on 2006-08-20
Tried that already, It doesn't work.

Thanks for the input :)

Martin

---

### Post by RudolfMDLT on 2006-08-20
Trust me, I know your pain(ATI 9600)! ](*,) 

This is how I got mine working:
[http://www.ubuntuforums.org/showthread.php?t=195845](http://www.ubuntuforums.org/showthread.php?t=195845)

Read through the first post end then read the 2nd last post! I think this might be what your looking for! If it works, please say so and if it doesn't say so to! 

Cheers!

---

### Post by Martin A on 2006-08-20
Thanks dude, I haven't looked at this one before. I'll try it and post back....

Martin

---

### Post by Martin A on 2006-08-20
Nope. Just as I thought I still get the MESA drivers from fglrxinfo.
I tried the method of using the "radeon" drivers but I'm still getting no direct rendering and glxgears shows <300fps. I really appreciate your help here :) . Any more suggestions? I don't think this card is ever going to work. I think I'm gonna forget this shit and go back to using Windows, it may suck but I need 3D acceleration for my work. 

Thanks again,

Martin

---

### Post by RudolfMDLT on 2006-08-20
Well if adding the modules by hand didn't work... Sory brew, I don't know. You could get an NVIDIA card, or go back to windows. :(

My advice would be to dual boot. Once you get to know ubuntu, windows feels really primitaive. True, 3D-rendering in windows is supported in greater amounts than in a Linux enviroment. I do video editing for some extra cash and dual boot to use that, but otherwise, i do everything in Ununtu.

But if your willing, please post your entire xorg config file and i'll have a look at it. 

/etc/X11/xorg.conf 

Cheers,

---

### Post by Martin A on 2006-08-20
Here it is. I think I'm going to buy an nVidia card, rather than going back to Windows....

One more thing, and I'm probably just being stupid, but right next to "BusID" It says PCI. Its supposed to say that, right? Even though I have an AGP card....? 

Thanks,

Martin

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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI RADEON 9250"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107E"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATi RADEON 9250"
	Monitor		"PHILIPS 107E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by RudolfMDLT on 2006-08-21
okay,

I notice 2 things:


1)Your running a Phillips variant on the 9200 flavor of ati's cards
2)Your card is not pure ati. Mine's a all in wonder pro but it's essentially stock Ati. Your card loads an extra module I2C. I2C is a circuit design invented by phillips in the  1980's. And there are known issues on it. I don't think that you will find the answer on the forum – I think your better off looking at google. Here's what i have found sofar:

[http://www.esacademy.com/faq/i2c/](http://www.esacademy.com/faq/i2c/) 
[http://lwn.net/Articles/189041/](http://lwn.net/Articles/189041/) 
[http://www.linuxhardware.org/](http://www.linuxhardware.org/)

The above is just some info, though the lwn.net is worth checking out. here:[http://www.linuxquestions.org/questions/showthread.php?t=354793](http://www.linuxquestions.org/questions/showthread.php?t=354793) are maby a couple of things you haven't tried?

Sorry to be the vringer of bad news but I havn't really found a success story with the 9250 range - Although they are supposed to be supported.


Just do me one favour. Change "	Driver		"radeon"" that to fglrx and remove double buffering =>  "Load	"dbe""


I really hope that this helps man! Goodluck! I'll check back here soon!

---

### Post by Martin A on 2006-08-25
Hey man, sorry I didn't reply earlier. I tried changing the driver to fglrx and removed double buffering but it didn't work. No matter though as I just bought an nVidia card, had 3d acceleration & XGL/Compiz running within the hour.

Thanks for all yur help, the open source community wouldn't be the same without people like you 8) 

Martin

---

### Post by RudolfMDLT on 2006-08-26
:D  - Within the hour! I swear i'm getting an Nvidia card before the weekend is over! :) I'm glad you got your system to work!

---

### Post by Greycloak on 2006-08-26
I was able to get my 9200 working perfectly with either option from the following page:

[http://wiki.cchtml.com/index.php?title=Ubuntu_Dapper_Installation_Guide&redirect=no](http://wiki.cchtml.com/index.php?title=Ubuntu_Dapper_Installation_Guide&redirect=no)

The 8.28.8 driver from ATI actually caused me less problems than the driver from the repository.

---

### Post by Darth Tux on 2006-08-26
I got my 9250 working with the latest 8.28.8 drivers. In earlier releases I had to used this [guide]("http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26"). 3D acceleration worked right off the bat with the new drivers and I added [ Option "AGPv3Mask" "0x00000002" ] to my xorg.conf under the "Device" section.I added that to stop random freezing and complete lock-ups I was experiencing in games. Hope this helps.

---

### Post by greatmetal on 2006-08-26
I still cant get my 9550 working :(

---

### Post by Kengee on 2006-08-26
> **Darth Tux said:**
> I got my 9250 working with the latest 8.28.8 drivers. In earlier releases I had to used this [guide]("http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26"). 3D acceleration worked right off the bat with the new drivers and I added [ Option "AGPv3Mask" "0x00000002" ] to my xorg.conf under the "Device" section.I added that to stop random freezing and complete lock-ups I was experiencing in games. Hope this helps.
Hello to all. 
I am an Ubuntu 6.06 amd64 user, 64bit installed.
ATI 1300 512mb, AGP card.
Have tried Wiki's methods 1 & 2, and all troubleshooting. 
Have only been partially successful, installing ati's 8.25.18 driver from a clean install using the --buildpkg Ubuntu/6.06 option and following the steps in this forum for Radeon R2xx.
I will give much more details next post.
Back to the quote:
Wondering if that device option would help me with my AGP X1300 512mb which has two pci-bus addresses 1:0:0 and 1:0:1. I have tried actually adding another instance of the Device entry in (Xorg.conf) for the ATI car using flgrx driver.  The only difference between the two entries is the address one showing 1:0:1.  Nothing happened, and it didn't crash either, it just ignored it.  I'm going to try that Option "AGPv3Mask" "0x00000002" and post results with more detail.

---


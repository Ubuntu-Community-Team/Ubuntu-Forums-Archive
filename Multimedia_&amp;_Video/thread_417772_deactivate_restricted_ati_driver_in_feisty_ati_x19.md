---
title: "deactivate restricted ati driver in feisty ati x1950 512 mb"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by grimmson on 2007-04-21
Hello all. hopefully i'm the first person to ask this dumb question. I've had a terrible time with my ati x1950 (512 mb version). thought I'd give feisty a try and noticed that easy restricted driver manager (that worked on my other pc w/ nvid flawlessly). Boy does ati suck. I've got a quad boot system up so I can surf for answers when I break a distro and I've done it again. When your restricted drivers lock your system at splash screen b 4 login, do you just sudo nano /etc/X11/xorg.conf and ati to vesa then remove the restricted ati driver after reboot in that nifty restricted driver manager to try a different driver install (envy on feisty?) or is there a slick command at recovery console to purge the ati driver and restore mesa? Any ideas for ati x1950 512mb in feisty? anone want a never fully utilized ati x1950 cheap? Thanks for any replies.

---

### Post by itsjustarumour on 2007-04-22
> **grimmson said:**
> Hello all. hopefully i'm the first person to ask this dumb question. I've had a terrible time with my ati x1950 (512 mb version). thought I'd give feisty a try and noticed that easy restricted driver manager (that worked on my other pc w/ nvid flawlessly). Boy does ati suck. I've got a quad boot system up so I can surf for answers when I break a distro and I've done it again. When your restricted drivers lock your system at splash screen b 4 login, do you just sudo nano /etc/X11/xorg.conf and ati to vesa then remove the restricted ati driver after reboot in that nifty restricted driver manager to try a different driver install (envy on feisty?) or is there a slick command at recovery console to purge the ati driver and restore mesa? Any ideas for ati x1950 512mb in feisty? anone want a never fully utilized ati x1950 cheap? Thanks for any replies.

Oh dear, Fiesty out on Thursday, for the first time ever my venerable NVidia card worked "out of the box"... and then on Friday it died.  Saturday I bought a brand new x1950 512MB AGP card, and..... ARG!  

I think I've made a bit of a boo-boo, haven't I?  8-[

Has anyone got this card to work in Fiesty yet?

---

### Post by itsjustarumour on 2007-04-22
Hmmm, I've tried "Envy", but it simply doesn't work.  The ATI website states the driver covers cards up to x1900, and Xorg up to 7.1.  Does this mean that the x1950 cards (and Xorg 7.2) are completely unsupported in Fiesty?  Anyone got any ideas for other solutions?  Or do I put my card up for sale on EBay?  :-(

---

### Post by teddmeister2 on 2007-04-22
could you post your xorg.conf file?

Also, I don't know if this helps, but according to the following articles, the proprietary linux drivers actually do work on x1950.  (The first URL is a benchmark test for certain games in linux using the x1950 (which uses a beta of fglrx 8.32.1), and the second URL says that ati's 8.32.5 driver officially supports X.org 7.2 and the x1950 card.  I'm not sure if this is the case, but that's what they say.
[http://www.phoronix.com/scan.php?page=article&item=601&num=3](http://www.phoronix.com/scan.php?page=article&item=601&num=3)
[http://www.phoronix.com/scan.php?page=article&item=603&num=1](http://www.phoronix.com/scan.php?page=article&item=603&num=1)

Also, I have an ati card, and ran the "restricted driver" installer (I previously was using the open source drivers with AIGLX for beryl), and it was not very nice to my system.  But I would recommend that you do NOT run the restricted driver installer on a edgy=>feisty upgrade, unless you want to have to screw around before getting x back up again.
But, anyway, that's about all I have to say for now.

---

### Post by itsjustarumour on 2007-04-23
> **teddmeister2 said:**
> could you post your xorg.conf file?

Also, I don't know if this helps, but according to the following articles, the proprietary linux drivers actually do work on x1950.  (The first URL is a benchmark test for certain games in linux using the x1950 (which uses a beta of fglrx 8.32.1), and the second URL says that ati's 8.32.5 driver officially supports X.org 7.2 and the x1950 card.  I'm not sure if this is the case, but that's what they say.
[http://www.phoronix.com/scan.php?page=article&item=601&num=3](http://www.phoronix.com/scan.php?page=article&item=601&num=3)
[http://www.phoronix.com/scan.php?page=article&item=603&num=1](http://www.phoronix.com/scan.php?page=article&item=603&num=1)

Also, I have an ati card, and ran the "restricted driver" installer (I previously was using the open source drivers with AIGLX for beryl), and it was not very nice to my system.  But I would recommend that you do NOT run the restricted driver installer on a edgy=>feisty upgrade, unless you want to have to screw around before getting x back up again.
But, anyway, that's about all I have to say for now.

Hi Teddmeister2,

Thanks for your post and the links, looks interesting.  The way I read it, the x1950 is officially supported now by both the 8.32.1 Beta and 8.32.5 drivers - and 8.32.1 only supports Xorg 7.1, but 8.32.5 is supposed to support Xorg 7.2 although the RC3 was unable to because of a bug - although bearing in mind the article was written in December 2006 hopefully this is fixed now(?)  

I'm at work at the moment but I'll post up my xorg.conf when I get home this evening.  I'm trying this on a brand new fresh install btw.  Like you, using the Restricted Drivers Manager produced a lot of problems (windows not drawing properly or being draggable).  And when I tried Envy, it seemed to install OK but the 3D acceleration still wasn't working...

Also - you mentioned Beryl - did you get this working OK on your ATI card?  I've seen a lot of posts saying that it was "impossible" to run Beryl on an ATI setup, but I'd really like to as I'm a big fan.

Anyway, thanks again for your post, and have a good day sir! :D

---

### Post by itsjustarumour on 2007-04-23
Well, still no joy.  I saw saw that Alberto Milone had released a new version of "unstable" Envy today with a fix for some ATI cards, so I tried a fresh install and gave that a go.  The (8.35.5) driver seems to install fine, but I still can't enable 3D acceleration!  And when I try going into the restricted driver manager, I get a message that "Your hardware does not need any restricted drivers"...  ](*,)

For the record, heres my current Xorg.conf:


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
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
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
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
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
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
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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


Anyone get any ideas what I'm doing wrong?  :rolleyes:  Has anybody else out there got 3D acceleration working on an ATI x1950-based card?

---

### Post by itsjustarumour on 2007-04-23
OK, I've tried a manual install of the (8.36.5) driver as per the how-to at "The Unofficial ATI Linux Driver Wiki" at:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

but I get as far as entering

> bash ati-driver-installer-8.36.5-x86.x86_64.run --buildpkg Ubuntu/feisty
 

and I get:

> bash: ati-driver-installer-8.36.5-x86.x86_64.run: No such file or directory


:-(   Is there something with the formating with the above command?  I'm not really au fait enough with the terminal yet to spot any errors!

---

### Post by teddmeister2 on 2007-04-24
For the command, you probably either have to navigate to the folder in which you have that file to execute that command or you have to enter the actual path to the file within the command.

With respect to your xorg.conf file, it seems that you might have a lot of problems...
...very thin options in ati driver
...*another device* listed with "vesa" as the driver

could you execute the commands glxinfo and fglrxinfo in a terminal and post the output?

Also, just in response to your question, I, though I only have an ati x300; have been able to get beryl to work both with fglrx + XGL   AND opensource drivers + AIGLX.  However, I haven't tried beryl yet in feisty, but I do have direct rendering with my ati card.

---

### Post by itsjustarumour on 2007-04-25
> **teddmeister2 said:**
> For the command, you probably either have to navigate to the folder in which you have that file to execute that command or you have to enter the actual path to the file within the command.

With respect to your xorg.conf file, it seems that you might have a lot of problems...
...very thin options in ati driver
...*another device* listed with "vesa" as the driver

could you execute the commands glxinfo and fglrxinfo in a terminal and post the output?

Also, just in response to your question, I, though I only have an ati x300; have been able to get beryl to work both with fglrx + XGL   AND opensource drivers + AIGLX.  However, I haven't tried beryl yet in feisty, but I do have direct rendering with my ati card.

Hi there Teddmeister2, thanks for your post.  You've certainly given me a couple of ideas for things to look at.  I've just done a clean install and I'm about to reinstall the latest Envy, but its looks like Alberto Milone's server is down at the moment.  As soon as I'm all done I'll post up the glxinfo and fglrxinfo output you mentioned.  

As an aside, I did post on Alberto's site yesterday RE Envy not working with my x1950 card and he pm'ed me back asking for further info, so that will be my official "bug report" submitted! I would much rather understand whats going on under the hood though, and work out a way of getting this working manually!  :-)

---

### Post by itsjustarumour on 2007-04-25
OK, back again.  Heres the output from glxinfo:

> ian@COOLERMASTER:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
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
ian@COOLERMASTER:~$  


And heres the output from fglrxinfo:

> ian@COOLERMASTER:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

ian@COOLERMASTER:~$ 



OK, those are with a clean updated install with the latest Envy.  Would it be more helpful if I re-installed again, and posted these up without installing Envy?  Being a bit of a Linux noob, I'm non too sure what half of this means!

Good to hear you got Beryl working anyway with your ATI card.  There seem to be so many people on the forums having trouble  :-)

---

### Post by grimmson on 2007-04-29
ok hijackers (just kidding), here is the original question in short form.

do you just sudo nano /etc/X11/xorg.conf and ati to vesa then remove the restricted ati driver after reboot in that nifty restricted driver manager to try a different driver install (envy on feisty?) or is there a slick command at recovery console to purge the ati driver and restore vesa?

---

### Post by teddmeister2 on 2007-05-02
grimmson,  If I remember correctly, the restricted driver manager isn't very smart, and doesn't revert the parts of xorg.conf that it changes when it adds the driver, so you may have to do some more editing of that to get your drivers the way the were before, but in terms of removing the driver all you *have* to do is replace fglrx with vesa and run ```
sudo apt-get remove xorg-driver-fglrx
``` and hit ctrl-shft-backspace (if you were able to load x in the first place) or type startx if you're in some sort of safe/commandline mode.
ITSJUSTARUMOUR: Check this link out to see if it will solve your problem: [http://www.thinkwiki.org/wiki/Problems_with_fglrx#Perpetual_Mesa_GLX_Indirect_on_Debian](http://www.thinkwiki.org/wiki/Problems_with_fglrx#Perpetual_Mesa_GLX_Indirect_on_Debian)
Make sure to read the info below before just trying the command.

---


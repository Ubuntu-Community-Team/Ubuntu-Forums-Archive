---
title: "ATI 9250se -- no 3D or TV-out in ubuntu -- help please?"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by CyberCod on 2006-07-09
I've read the other threads in here concerning this card, but they tend to make assumptions about the amount of knowledge the reader has concerning how to follow the instructions.

I've been using Ubuntu Dapper for a little over a week now, and I'm ready to switch full time, away from XP, but in order to do so, I need to get my 3D support and TV-out working.


Kernel is Ubuntu 2.6.15-25-386


I'm currently using the xorg-driver-fglrx-ati... (i think)

i have the following packages installed

fglrx-control
fglrx-kernel-source
xorg-driver-fglrx-dev
xorg-driver-fglrx-ati


fglrxinfo gives me
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```


glxinfo gives me

```

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
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow

```



lspci gives me
```

0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
0000:01:07.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 01)
0000:01:0a.0 Ethernet controller: Linksys, A Division of Cisco Systems WMP11v4 802.11b PCI card
0000:02:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

```



my xorg.conf is as follows:

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
	Screen         "Default Screen" 0 0
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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver      "radeon"
	
	BusID       "PCI:2:0:0"


EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection



```


By changing Driver to "fglrx" and hitting CTRL+ALT+Backspace it comes up to login screen with crt displaying very high gamma and TV is still garbled.

I can then use "aticonfig --tv-format-type=NTSC-M" in the terminal and reload x again to get the TV-out working good, but crt is still high gamma.  This semi-progress is all thats keeping my wife from killing me at this point for spending the last few days in front of the monitor to the exclusion of all other things human.

Also upon rebooting, tv-out is garbled, and crt is fine up until it starts to load the gui login, and then both screens are completely garbled.  So apparently something is amiss.


I then must CTRL+ALT+F2 to get back to command line, and 
"cp /etc/X11/xorg.conf_original /etc/X11/xorg.conf" and reboot once again to get back to my normal configuration.

I don't know what "make" is.

I don't know how to compile a kernel.

I don't know a lot of the things that you may find 2nd nature by now.  In windows I am a god.  In here, I'm a chump.

I have downloaded the proprietary ati drivers, but they're in rpm format and don't seem to want to install.  I got a tip to use "alien -i -d" on them, but it did not want to go through.  I cannot remember the error message.

While I realize that this is probably a bit ambitious a task for someone who's only been using linux for a week, I'm a pretty avid searcher of information and can usually figure things out quickly.

Someone called me a troll.  

I've not been a noob for a long time, but I'm finding that unlearning windows stuff to be the hardest part about all of this.

I don't think that linux needs to be more like windows... in the coming days with the $100 linux laptops for 3rd world countries, I believe MS will end up with a niche market-share like Mac currently has.  Linux will be the One OS to Rule them All.  I'm trying to stay ahead of the wave.

I just don't know what I'm doing yet. :confused: 


If there's anyone who has the patience to help me out, and doesn't mind me asking repeatedly "And what does that mean?" I would greatly appreciate it.

I have read approximately 50 pages of stuff related to this and have yet to come up with the solution, or a detailed step-list of what to do.  I'm not adverse to reading, so if there IS a page out there that you know of, I'd be very thankful to check it out.

When finished, I hope to write an extremely detailed page for new users on what to do in this situation.


Other specs:

AMD Athlon 1.8Ghz
512MB PC3200 system ram
nVidia nForce2 M7NCD motherboard
creative soundblaster live VE
Linksys wireless-b pci card loaded with ndiswrapper

Once I can play games (via cedega) and watch stuff on the tv, its bye bye windows.  I just need a little help getting there.  Everything else I do with windows, I've pretty much figured out how to do with ubuntu already.

I appreciate your time in reading this and look forward to any help  or advice I receive.


-------------------------------------------------

UPDATE

I've now made a launcher to swap the TV-enabled xorg.conf for the original one.  And another one to change it back from a copy of the original.

So as of right now, I can boot up, run TV Switch launcher and hit CTRL+ALT+Backspace to reload x, and I have my TV working (with high gamma on the crt).

Then before rebooting I MUST remember to launch Switch Back and reload x again. (I think it saves xorg.conf on exiting so it must be reloaded before rebooting)

I do not know why it won't cold start to the tv version of xorg.conf

I tried the instructions found at [BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") 
pretty much to the letter and got nothing.  And I mean nothing.  Monitor switched off, TV went the typical "no-signal" shade of blue.

Still reading other sites.  About to start a help session on [Qunu]("http://alpha.qunu.com/index.html#").  Again.

Wish me luck!

Below is the text of my file xorg.conf_tv 
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
	Screen         "Default Screen" 0 0
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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver      "fglrx"
	VideoRam    131072
	Option	    "TVFormat" "NTSC-M"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```




----------------------------------------------------------

UPDATE 2

I've gotten to the point where I've gotten rid of the gamma problem by using    Option "SWcursor" "on" & Option "HWcursor" "off" but like other users at this stage, it gives residual artifacts behind the mouse.  It also doesn't hold through a reboot.  Rebooting with this xorg.conf active nets me blank screens as in "no signal"

I'm still working on this feverishly.

Using Option GammaCorrectionI makes no difference.


Also, is there a way to put multiple commands in the launcher command line?

I'd like to simulate the Ctrl+Alt+Backspace to take out a step of the process.  

Also if there's a way to automate these two launchers at startup and shut down, then I just need to figure out how to get rid of cursor artifacts, and then I can start working toward the 3D side of all this.

Any help would be appreciated.  And if there are any awesome gurus out there who have done all this and it leads to a dead end, just let me know, so I can stop wasting my time, and start firing off hatemail at ATI for their poor linux support.

---

### Post by CyberCod on 2006-12-12
--UPDATE--


I ended up buying a used nVidia card and it works wonerfully.  Since then ATI has merged with AMD.  I am not sure how their driver support has changed since this happened, but I will be trying them out again soon as I'm giving the ATI card away along with installing linux for a friend as a Christmas gift.  I will further update this thread when that is accomplished.  I will also be trying out 6.10 at that time, and perhaps an off-shoot of ubuntu called Mint.

---


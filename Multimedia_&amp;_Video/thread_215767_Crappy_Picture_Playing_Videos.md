---
title: "Crappy Picture Playing Videos"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by twoseids on 2006-07-14
On Dapper, my picture looks awful when I watch DVDs or video files. This is on Movie Player, by the way. It looks a bit better if I use MPlayer, but it's still so bad I just reboot and go into Windows.

My brothers, this should not be.

How can I troubleshoot my Movie Player to get it working as it should?

---

### Post by bojzi on 2006-07-14
Do you have totem-xine, the dvd css library and the w32codecs? Try [EasyUbuntu]("http://easyubuntu.freecontrib.org/")...

---

### Post by twoseids on 2006-07-14
> **bojzi said:**
> Do you have totem-xine, the dvd css library and the w32codecs? Try [EasyUbuntu]("http://easyubuntu.freecontrib.org/")...
Yes, I have those. I have run EasyUbuntu and Automatix previously. I notice that I have "totem" but not "totem-gstreamer". If I want to install "totem-gstreamer" I'm told I have to uninstall "totem-xine" - so I didn't do it.

---

### Post by bojzi on 2006-07-14
Did you setup your graphic card drivers? That's about the only thing that comes to my mind right now...

---

### Post by twoseids on 2006-07-14
> **bojzi said:**
> Did you setup your graphic card drivers? That's about the only thing that comes to my mind right now...
What's the command to find out what graphics card I have? Sorry, might be a dumb question.

---

### Post by bojzi on 2006-07-14
Well, basicly when you type "dmesg" into the Terminal you should see if you're using Nvidia or ATI (or something third like an Intel integrated card - i915). If using ATI you should go for the fglrx drivers (I think that's available in EasyUbuntu as an automatic install script). As I don't have an Nvidia card, I can't help you there (just search the forums on howto install Nvidida card drivers).

---

### Post by twoseids on 2006-07-14
> **bojzi said:**
> Well, basicly when you type "dmesg" into the Terminal you should see if you're using Nvidia or ATI (or something third like an Intel integrated card - i915). If using ATI you should go for the fglrx drivers (I think that's available in EasyUbuntu as an automatic install script). As I don't have an Nvidia card, I can't help you there (just search the forums on howto install Nvidida card drivers).
I think it's an Intel card, but the "dmesg" command gave me like 6 pages of stuff to sift through. I have to bolt right now, so I'll run it again later and look through it to find out which card it is. Thanks!

---

### Post by twoseids on 2006-07-14
> **bojzi said:**
> Well, basicly when you type "dmesg" into the Terminal you should see if you're using Nvidia or ATI (or something third like an Intel integrated card - i915). If using ATI you should go for the fglrx drivers (I think that's available in EasyUbuntu as an automatic install script). As I don't have an Nvidia card, I can't help you there (just search the forums on howto install Nvidida card drivers).
I have an Intel GMA 950. I've searched the forums and it doesn't look like anyone knows what to do yet with these cards. I believe I have an Intel i810 driver (where do I check?) installed for this, but um, it sucks.

---

### Post by bojzi on 2006-07-15
> glxinfo

Try this command in the Terminal and copy-paste the results here, it should tell us what's up with the card (if the drivers are installed).

Edit:
And could you please copy-paste the contents of your /etc/X11/xorg.conf file?

---

### Post by twoseids on 2006-07-15
> **bojzi said:**
> Try this command in the Terminal and copy-paste the results here, it should tell us what's up with the card (if the drivers are installed).

Edit:
And could you please copy-paste the contents of your /etc/X11/xorg.conf file?

glxinfo:

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
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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

```

/etc/X11/xorg.conf:

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
	Load	"bitmap"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel GMA 950"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	8192
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel GMA 950"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by bojzi on 2006-07-15
Your glxinfo tells me that you don't have the right drivers installed. There's a nice page on the wiki that shows how to install the appropriate drivers for Intel graphic cards.
It's located here -> [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)
Actually, I think that doing "sudo apt-get install 915resolution" in the Terminal should do the trick (because the rest of the wiki page pretty much handles how to get non-standard resolutions). Just be sure you have the universe and multiverse Repositories enabled (and if you don't know what I'm talking about take a look here -> [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) under the section "Adding the Universe and Multiverse Repositories").

After installing the driver try to use the glxinfo command again (a restart may be necessary) and see if the next lines have changed:
> direct rendering: No
This should change to "direct rendering: Yes"
> OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
The second line should change to your card type instead of the Mesa GLX Indirect.

Let me know if it works...

---

### Post by twoseids on 2006-07-16
> **bojzi said:**
> Your glxinfo tells me that you don't have the right drivers installed. There's a nice page on the wiki that shows how to install the appropriate drivers for Intel graphic cards.
It's located here -> [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)
Actually, I think that doing "sudo apt-get install 915resolution" in the Terminal should do the trick (because the rest of the wiki page pretty much handles how to get non-standard resolutions). Just be sure you have the universe and multiverse Repositories enabled (and if you don't know what I'm talking about take a look here -> [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) under the section "Adding the Universe and Multiverse Repositories").

After installing the driver try to use the glxinfo command again (a restart may be necessary) and see if the next lines have changed:

This should change to "direct rendering: Yes"

The second line should change to your card type instead of the Mesa GLX Indirect.

Let me know if it works...
The direct rendering is still "No" but the three lines beginning with "OpenGL" are exactly as you've put them in your code above.

Also, in my /etc/X11/xorg.conf file, it still says "i810" for the driver. Does that matter?

---

### Post by bojzi on 2006-07-16
> **twoseids said:**
> The direct rendering is still "No" but the three lines beginning with "OpenGL" are exactly as you've put them in your code above.

Also, in my /etc/X11/xorg.conf file, it still says "i810" for the driver. Does that matter?

Exactly as in my code? You mean it still says: "OpenGL renderer string: Mesa GLX Indirect"?

If that's so then it didn't work...

Did you reboot after the installation of the drivers?

I can't think of anything else on how to install the drivers correctly, maybe someone else has any more experience in Intel graphic cards because I never had one. And I do think that it should say i810 in the xor.conf file...

I see that you've replied into another thread where someone else has the same problem.

Looks like people had success with this tutorial here -> [http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/](http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/) although it's just a little rewrite from the wiki one. Maybe you should try to add the 915resolution to your /etc/init.d/bootmisc.sh with the option for your desired resolution. Maybe it needs to be autostarted...

---

### Post by twoseids on 2006-07-17
> **bojzi said:**
> Exactly as in my code? You mean it still says: "OpenGL renderer string: Mesa GLX Indirect"?

If that's so then it didn't work...

Did you reboot after the installation of the drivers?

I can't think of anything else on how to install the drivers correctly, maybe someone else has any more experience in Intel graphic cards because I never had one. And I do think that it should say i810 in the xor.conf file...

I see that you've replied into another thread where someone else has the same problem.

Looks like people had success with this tutorial here -> [http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/](http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/) although it's just a little rewrite from the wiki one. Maybe you should try to add the 915resolution to your /etc/init.d/bootmisc.sh with the option for your desired resolution. Maybe it needs to be autostarted...
First of all, bozji, thanks a lot for hanging in there and continuing to answer my inquiries. You're part of the spirit that really makes Ubuntu work - an actively involved community helping others!

To answer your questions:

* yes, that line in "glxinfo" still says, "OpenGL renderer string: Mesa GLX Indirect"
* yes, I rebooted

I tried that 915resolution fix. Apparently I already had it installed - maybe it was one of the things I tried? Anyway, I haven't put it in the "bootmisc.sh" file. Where exactly should I put it? And what should the line look like? In the guy's HOWTO, the location is /usr/bin/915resolution, but he's running SUSE so maybe it's different. I can't find a "915resolution" directory OR file anywhere on my computer (though I successfully ran the command from terminal).

I'm probably just confused as to directories, files, etc.

---

### Post by bojzi on 2006-07-18
No problem, mate, I've been helped here so many times it would be just wrong not to help out. :)

Anyways, you can use the part at the Ubuntu Community help (the link that I gave you earlier) -> [https://help.ubuntu.com/community/i915Driver#head-afc0b5f2adbc8a5842aa259c4d8f6d3d32abe5f7](https://help.ubuntu.com/community/i915Driver#head-afc0b5f2adbc8a5842aa259c4d8f6d3d32abe5f7)

In a nutshell:
Type
```
sudo gedit /etc/init.d/915resolution
```
ito the terminal then paste the following code into it:
```
#! /bin/sh

/usr/bin/915resolution _insert_desired_resolution_here_
```
where the _insert_desired_resolution_here_ presents the place for your desired resolution that you got from the "sudo 915resolution -l" (for example -> "/usr/bin/915resolution 38 1280 800").

Now just click on Save in the Text Editor and close it.
After this run
```
update-rc.d 915resolution start 99 defaults
```
in the terminal to ensure that the 915resolution is started each time your OS starts up.

Now try to reboot and see if it works...

Note that this should work for Ubuntu (no fear of it being for SUSE) because it was written directly for Ubuntu on the already mentioned page. ;)

---

### Post by twoseids on 2006-07-26
> **bojzi said:**
> 
Type
```
sudo gedit /etc/init.d/915resolution
```
ito the terminal then paste the following code into it:
```
#! /bin/sh

/usr/bin/915resolution _insert_desired_resolution_here_
```
where the _insert_desired_resolution_here_ presents the place for your desired resolution that you got from the "sudo 915resolution -l" (for example -> "/usr/bin/915resolution 38 1280 800").

Now just click on Save in the Text Editor and close it.
After this run
```
update-rc.d 915resolution start 99 defaults
```
in the terminal to ensure that the 915resolution is started each time your OS starts up.

Okay, did that. Now my /usr/bin/915resolution file says:

```
#! /bin/sh

/usr/bin/915resolution 5c 1024 768
```

But when I tried to do ```
update-rc.d 915resolution start 99 defaults
``` I got this:
```
eric@ubuntu:~$ update-rc.d 915resolution start 99 defaults
update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
```

---

### Post by bojzi on 2006-08-03
I'm not too good with such advanced stuff :), but google looks like it is. :)

Basicly, there should be a dot added in the command, like they had to do for the command on this page: [http://www.mobile-ipv6.org/pipermail/mipl/2003-October/005600.html](http://www.mobile-ipv6.org/pipermail/mipl/2003-October/005600.html) .

My suggestion is to try and run the command as this:

```
update-rc.d 915resolution start 99 defaults .
```
(notice the dot (.) at the end of the command)

Another example of the dot problem:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=4180#p4180](http://forum.ubuntu-fr.org/viewtopic.php?pid=4180#p4180)

Of course, you can always start the script by hand each time you boot up (or just to check if it works) by typing:
```
/etc/init.d/915resolution start
```

---

### Post by ssergeje on 2006-08-18
Hei! I've got HP nx6310 laptop with Intel i945GM chipset with Intel GMA950 graphics.
I experience the same problem. The videos in Totem(gSteamer) and VLC are waay too dark, with Totem-xine they are way too light. It doesn't play Ogg/Theora at all
```
:~$ totem desktop-recording.ogg
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 45 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```.

```
:~$ vlc desktop-recording.ogg
VLC media player 0.8.4 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  80
  Current serial number in output stream:  81

```

```
:~$ mplayer desktop-recording.ogg
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel  (Family: 6, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing desktop-recording.ogg.
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
Ogg file format detected.
VIDEO:  [theo]  1024x768  24bpp  2.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x86fd3e8]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1024 x 768 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1024x768 => 1024x768 Planar YV12
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
Audio: no sound
Starting playback...
X11 error: BadAlloc (insufficient resources for operation)


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20050225
OpenGL version string: 1.3 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

```

I changed the drive in my xorg.conf from "i810" to "vesa" and everything works smooth for now, except 3D... :???:

---

### Post by n0yd on 2006-08-20
I get this problem also on both my notebooks using the i810 driver (One is a 845 and the other 945GM), in totem (using totem-xine I think, because automatix and easyubuntu both remove totem-gstreamer) the picture almosts looks like a light bulb is shining on it, everything is to bright. But in MPlayer and VLC everything seems to work fine...

---

### Post by ssergeje on 2006-09-09
Cheers!
The linux freedom of choise won this one! 
I installed 
```
totem-xine libxine-extracodecs libxinerama1 w32codecs
```
Then I went to Totem EDIT > PREFERENCES, display tab; there I adjusted brightness and stuff.
Now I can play all my videos and movies. The scrolling of the movie doesn't freeze totem (like it did with GStreamer), I can play ogg (though it seems to play slower (look my previous post) ), wmv, avi and stuff.
VLC doesn't play some WMVs, MPlayer yells something about XVideo unaccesibility.
Go-go Xine, the freezed, but STABLE project :biggrin:

---


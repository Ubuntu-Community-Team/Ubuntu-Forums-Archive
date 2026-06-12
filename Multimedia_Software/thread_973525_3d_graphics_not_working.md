---
title: "3d graphics not working"
date: 2008-11-06
forum: Multimedia Software
---

### Post by Philip Hammer on 2008-11-06
I just recently installed ubuntu 8.10. I am having trouble with my 3d graphics. when I try to launch an application that uses 3d graphics like blender the program starts causes garbage on the screen and then closes. also the screensaver preview doesn't work with 3d screensavers. when I try to preview them it just causes lines across the bottom of my screen. All 2d applications work without any graphic problems. I have a compaq presario 5000 series with an intel pentium 3 and and intel i810 chipset.

any help would be greatly appreciated.

---

### Post by Philip Hammer on 2008-11-06
I just recently installed ubuntu 8.10. I am having trouble with my 3d graphics. when I try to launch an application that uses 3d graphics like blender the program starts causes garbage on the screen and then closes. also the screensaver preview doesn't work with 3d screensavers. when I try to preview them it just causes lines across the bottom of my screen. All 2d applications work without any graphic problems. I have a compaq presario 5000 series with an intel pentium 3 and and intel i810 chipset.

any help would be greatly appreciated.

---

### Post by Philip Hammer on 2008-11-06
I just recently installed ubuntu 8.10. I am having trouble with my 3d graphics. when I try to launch an application that uses 3d graphics like blender the program starts causes garbage on the screen and then closes. also the screensaver preview doesn't work with 3d screensavers. when I try to preview them it just causes lines across the bottom of my screen. All 2d applications work without any graphic problems. I have a compaq presario 5000 series with an intel pentium 3 and and intel i810 chipset.

any help would be greatly appreciated.

---

### Post by Philip Hammer on 2008-11-06
I just recently installed ubuntu 8.10. I am having trouble with my 3d graphics. when I try to launch an application that uses 3d graphics like blender the program starts causes garbage on the screen and then closes. also the screensaver preview doesn't work with 3d screensavers. when I try to preview them it just causes lines across the bottom of my screen. All 2d applications work without any graphic problems. I have a compaq presario 5000 series with an intel pentium 3 and and intel i810 chipset.

any help would be greatly appreciated.

---

### Post by sirebral on 2008-11-06
A couple of questions:

Are you running Compiz?
Have you been using the Proprietary driver?

---

### Post by anjilslaire on 2008-11-06
You may have an nvidia or ati GPU, depending on which 5000 model you have. Try enabling the Restricted Driver manager under the System menu.

---

### Post by Philip Hammer on 2008-11-06
I am not sure what compiz is. I have not been using the proprietary driver or at least none shows up in Hardware Drivers.

---

### Post by Philip Hammer on 2008-11-06
I have intel integrated graphics (i810)

---

### Post by pytheas22 on 2008-11-06
Did you try turning off desktop effects before starting Blender?  That could be the problem.

Some of the older i810 chips also just don't work very well with modern 3d applications.  If you have a Pentium III, I'm guessing your machine is a bit dated.  If you post the output of this command, we can look up your chipset to see if the i810 driver is supposed to support 3d acceleration for your card:
```

lspci -nn
```

---

### Post by Philip Hammer on 2008-11-06
someone please help!

---

### Post by Philip Hammer on 2008-11-06
someone please help!

---

### Post by Philip Hammer on 2008-11-06
I never run the desktop effects. mostly because they won't start.
here is the output:
00:00.0 Host bridge [0600]: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub [8086:7124] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller [8086:7125] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus Controller [8086:2413] (rev 02)
01:05.0 Multimedia audio controller [0401]: ESS Technology ES1988 Allegro-1 [125d:1988] (rev 12)
01:0b.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)

---

### Post by Philip Hammer on 2008-11-06
help please!

---

### Post by pytheas22 on 2008-11-06
If compiz won't work, then it's probably an issue of lack of real 3d support.  If you try to start blender from a command-line, what is the output that gets dumped to the terminal?  It might say specifically why it doesn't want to start.

Also, according to [this thread]("http://ubuntuforums.org/archive/index.php/t-655639.html"), if you comment out lines 229-232 of your /usr/bin/compiz file, compiz will start on your card (can't guarantee that that information is still current).  If that's true, then your card must support 3d acceleration.

Another possible problem is that the card is not being given enough shared memory.  Did you check your BIOS to see how much you're sharing with the integrated graphics?

---

### Post by overdrank on 2008-11-06
Please do not create multiple threads on the same issue. Threads Merged.

---

### Post by Philip Hammer on 2008-11-06
sorry, I was not sure which forum would give the best results. blender comes up with a segmentation fault. how would should you edit the compiz file it is write protected?

---

### Post by pytheas22 on 2008-11-06
What exactly was the terminal output in blender?  If it's segfaulting, the problem probably has to do with blender itself, not your video driver.  Have you tried running any other 3d programs?  You can install Tux Racer, a 3d game, by typing:
```

sudo apt-get install planetpenguin-racer
```

When it's installed, run it from your Applications>Games menu.  Does that work?

> 
how would should you edit the compiz file it is write protected? 

You might need to make it writeable first.  Try opening it for editing by typing these commands:
```

sudo chmod +x /usr/bin/compiz
sudo gedit /usr/bin/compiz
```

The file should open and you should be able to edit it and save your changes.

---

### Post by Philip Hammer on 2008-11-06
tux racer was to scrambled to play. I tried commenting out the lines in the compiz file and got:

/usr/bin/compiz: 233: Syntax error: "fi" unexpected (expecting "}")

when I tried to run compiz again.

---

### Post by sirebral on 2008-11-06
What kind of errors does you console display when you run a 3D app?

---

### Post by Philip Hammer on 2008-11-06
here is the exact terminal output for blender:

philip@philip-desktop:~$ blender
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Segmentation fault

---

### Post by Philip Hammer on 2008-11-07
> **sirebral said:**
> What kind of errors does you console display when you run a 3D app?

what do you mean?

---

### Post by pytheas22 on 2008-11-07
There are some suggestions [here]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg426753.html") regarding solving the blender segfaulting.  Or google [blender segmentation fault]("blender segmentation fault") and you'll find some other stuff.  If you don't understand what the suggestions mean, let me know and I'll tell you more specifically what you should do.  I think that blender crashing has more to do with problems with blender than with your 3d acceleration configuration.

As for getting compiz working, try commenting out lines 230-233 of your /usr/bin/compiz file (make sure 229 is not commented).  It doesn't make sense to comment 229-232 of the file that exists in Intrepid (the instructions that I found saying to comment those lines were based on an older version of compiz).  If that doesn't help, what do you get if you type in a terminal:
```

compiz --replace
```

Also, what is the terminal output if you type:
```

ppracer
```

And is the penguin game just too slow to be playable (which could just mean that you have a weak graphics card), or do you actually see garbage on the screen when you try to play it?

Finally, what is the output of:
```

glxinfo
```

---

### Post by Philip Hammer on 2008-11-08
commenting out line 230-233 instead of 229-232 gets rid of the syntax error but, compiz sill does not run.

here is the output for compiz --replace:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x864) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity
```

Here is the output for ppracer:
```
PPRacer 0.3.1 --  http://racer.planetpenguin.de 
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.
```

I actually see garbage when I play it. When I close pprace some of the lines remain on the desktop until I move a windows over them.

the output for glxinfo is:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Keith Whitwell
OpenGL renderer string: Mesa DRI i810E 20050821 x86/MMX/SSE
OpenGL version string: 1.2 Mesa 7.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_compression, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

3 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x3c 32 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x3d  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x3e  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x3f  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x40  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x41  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x42  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x43  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x44  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x45  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x46  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x47  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x48  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x49  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x4a  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4b  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x4c  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
```

---

### Post by pytheas22 on 2008-11-08
Compiz doesn't seem to like the screen resolution that you're using.  Does it start if you switch to 1024x768 resolution?

---

### Post by Philip Hammer on 2008-11-08
I set my computer to 1024x768 and ran compiz again, and my computer screen filled with garbage and then it locked up. So I restarted it and logged into my account and my computer crashed again the same way. Probably because it tried to load compiz again.

---

### Post by pytheas22 on 2008-11-08
I'm really sorry that that happened.  You should be able to get back to a normal screen if after logging into your garbage-filled desktop you press alt-F2, then type *metacity --replace* and press enter (even if you don't see anything, just type it and press enter).

If that fails, the next best thing would be to boot Ubuntu, and before logging into the desktop, press control-alt-F2.  You will be brought to a command prompt.  Log in, then run this command to uninstall compiz:
```

sudo apt-get remove compiz
```

Then restart your computer, and compiz should be gone.

The only other suggestion I can make at this point is that you try using the i810 driver instead of the the intel one for your video card.  i810 is an older driver; Ubuntu 8.04 and up use intel by default.  But i810 should still work and may perform better.  You can install it by typing:
```

sudo apt-get install xserver-xorg-video-i810
```

Then try running 3d applications again.

If that doesn't help, I'm out of suggestions; the only other thing I can recommend that you do is [file a bug report]("https://launchpad.net/ubuntu/+filebug/+login").

---


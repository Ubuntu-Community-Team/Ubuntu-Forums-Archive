---
title: "Via UniChrome PRO with Ubuntu 8.04"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by Firehalk on 2008-03-16
I don't know if I can open some thread related to an unreleased version (using alpha6 here with all updates installed), but since I saw some topics about Hardy Heron distro, I will make this one too. (If I cant, sorry, just say).

Anyone here with Via/S3G Unichrome PRO IGP tried Ubuntu 8.04?

Here my problem with 7.10 (the driver not working and not able to go into desktop) is solved now :) 
 I can use the OS with no problems and change resolution bigger than 1024x768.

But, with OpenChrome drivers I'm not able to set Ubuntu to use some special effects. When I click on any of the 2 other options, it says its unable to activate them. It will be forever like that with my VGA or it's because i need to change drivers?

I checked [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) but they still didn't release nothing to 8.04 (because it's not final I guess). When trying to use the 7.10 driver, it says its only compatible with that version.

Well, the main reason to open this thread is also to exchange information with other people that uses this VGA, and to know if anyone was able to run it fine with it or encountered some errors/problems too.

Of course, any help is well appreciate also.

Thanks a lot.

---

### Post by uhappo on 2008-03-24
I installed Ubuntu 8.04 Beta today, and finally I'm able to use my laptop!!!

VIA Unichrome Pro IGP works now.

It is a bit sluggish, but only a little.

---

### Post by y0umebednow on 2008-04-29
i have a MAJOR issue with this 8.04 version...
im only able to set my resolution up to 800x600

i went to screens and resolution (took me a while to find because its not in the "system" drop down menu..) and on 7.10 i was using the regular s3 - Unichrome driver. So thats what i chose and when i click on "Test" it gives me an error saying "Configuration test failed Please verify the selected devices and configuration."

this sucks. anyone having the same problem or know the solution?

sorry im not trying to hijack your thread but i thought you had the same problem.

---

### Post by metalmadhouse on 2008-05-06
well this chipset's been a real pain in the *** since I'm using ubuntu...

I managed to get my screen resolution up to 1600x1200 in hardy using the OpenChrome driver, also I get direct rendering in glxinfo and over 1000fps in glxgears with this cheap vga chipset, not bad huh...? 

but here comes the sad part, my rendering is all messed up! I can't watch dvd's or any high quality movie, any rendered games, anything without my screen going out of range or something like that! this is hell! I have rendering but I can't even enable Compiz without my desktop crashing and forcing me to restart xserver, even tho I use SKIP_CHECKS=yes, I don't mind about compiz, but no movies or Xmoto? :O come on! 

hopefully the people from Via Arena will put out some Unichrome driver for Hardy any soon...???

if someone has compiled a better driver than OpenChrome please give us some help! othewise I'll have to burn my Mobo hehe lol

---

### Post by inportb on 2008-05-06
It's not an Ubuntu problem. Heck, it's not even a Linux problem. VIA's had a terrible history. Supposedly, they're cooperating with the opensource community now; but unfortunately, they don't seem to understand what opensource is about.

---

### Post by lunchbox330 on 2008-05-06
Yeah, i'm stuck at 800x600 with the generic vesa driver myself, I just bought this new Everex thinking it was so Open Source friendly and, well, guess not. OpenChrome is even worse (640x480) so it looks like i'll be going video card shopping soon unless Via starts writing some drivers...

---

### Post by nayk on 2008-05-10
I found this post while trying to look for a solution to my problem. I've been using VIA for the past few years, and have had a mixed result with my Linux distros. The openchrome driver was a boon, and worked for both Ubuntu and openSUSE (and I guess it's not safe to say it here, but I'll still say it... that pcLinux didn't need that driver). 

Anyway, when I installed Ubuntu, it obviously did not recognise my screen resolution (it never does), so I installed the openchrome driver in Ubuntu 8.04 knowing that it wasn't supported and this is what happened. 

1. nothing for a while. 
2. Then I when to screen resolution settings and changed the resolution to 1024/768 (I think I should have tried this before assuming that the openchrome was the solution to my resolution problems)
3. Then when I restarted, and logged on it gave me a resolution of 800/600
4. Then when I logged out and logged back on, I got the resolution that I had opted for 1024.

5. Now, every time I start Ubuntu, I get a 800/600 resolution and then I have to log off and log back on, and then I get my full resolution. 

Not, pretty, I know, but that's what I'm doing at the moment. 

[http://alternativenayk.wordpress.com](http://alternativenayk.wordpress.com)

---

### Post by Nelis on 2008-05-10
I have the very same problem with my VIA EN12000 mobo
and when I want to start up Xubuntu (8.04), a menu appears saying that xubuntu is running in "safe graphics mode".

Selecting the right videodriver (S3 unichrome) does'nt help either, when I want to test the selected driver it says:
"Configuration test failed Please verify the selected devices and configuration."
:(

---

### Post by uhappo on 2008-05-11
Aargh,

I had to do a fresh install, and now I'm stuck with 800x640-reso. I had previously 1024x786-reso.

My laptop has via K8M800 UnichromePro-chipset.

So someone with a working setup... Help!

---

### Post by karelj on 2008-05-12
I suggest to change xorg.conf DefaultColorDepth to 16
and comment-out all Subsection lines for Depth 24.
So you will have enough memory to use vesa mode with 1027x768.

---

### Post by whatever69 on 2008-05-12
I have just the regular UniChrome, and it was running off of 6.06 at 1600x1200 to my Samsung LN40A530 LCD TV through VGA.  Now I'm stuck at 800x600 after doing my fresh install to 8.04.  

I have no idea if I should:

A.  Wait for VIA to release a version for 8.04 - [http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=101](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=101)
B.  Use OpenChrome - [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
C.  Continue hacking up xorg.conf - man xorg.conf

I really hate C.  It causes me to :cry:

For now, I control my Ubuntu machine through Screen Sharing on my macbook.

---

### Post by whatever69 on 2008-05-12
Hopefully this will be good news for us in a month or so as things are still in beta right now.  Keep checking this page:  [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
And this is via's forum specifically related to Linux: [http://www.tkarena.com/forums/linux-arena/](http://www.tkarena.com/forums/linux-arena/)

Got this info after reading this:  [http://www.phoronix.com/scan.php?page=news_item&px=NjQ2Nw](http://www.phoronix.com/scan.php?page=news_item&px=NjQ2Nw)

> VIA Gives 16,434 Lines Of OSS Code
Posted by Michael Larabel on May 08, 2008

Back at the Linux Foundation Austin Summit, VIA had announced plans to develop a new open-source initiative in a similar fashion what AMD has been doing. However, in the weeks following that they haven't done much for the open-source community. As was highlighted in VIA's Open-Source Efforts A Bluff?, their Linux website just contains two binary drivers right now and not much of anything else -- not even bug tracking software or a mailing list. This has upset some, but fortunately VIA has stepped up to the plate and shown they are actually doing more than a media blitz. 

VIA has released over 16,000 lines of code that provides a frame-buffer driver in the Linux kernel. This code is licensed under the GNU GPLv2 and appears to be crafted by VIA's Joseph Chan. Supported by this driver is VIA's Unichrome CLE266, K400, K800, PM800, CN700, CX700, K8M890, P4M890, P4M900, and VX800 IGPs. We're still pouring over the code, but it seems to be in pretty good shape and does support digital connections (and does seem to support HDMI already) -- in other words it appears to be further along than when the RadeonHD driver started out. 

This current work comes as nine patches presented on the linux-fbdev-devel mailing list (a few VIA patches). 

Kudos go out to VIA Technologies this morning for this code dump, but the work isn't over. They still have a lot of work left to do to mend relations with the Unichrome and OpenChrome projects and focusing upon 3D and video playback work, etc. However, this is a step forward in showing that VIA may actually come around this time and play ball with the open-source community.

---

### Post by angrybunny on 2008-05-17
for those having trouble changing screen resolution try ..system..main menu..look on the left for the 'other' tab..then tick the screens and graphics box.. then.. applications...other..screens and graphics.. and have at er.. this worked for me...but im still unable to escape the low graphics mode

---

### Post by whatever69 on 2008-05-17
I got the via driver loaded and can now do 1024x68.  That's the max that's avaible in in the resolutions drop down list.  1920x1080 or 1280x720 don't work.  Here's my working xorg.conf file.


Video Card = CLE266 Unichrome Chipset
Monitor = Samsung 40" LCD TV (LN40A530)
xorg.conf:


```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"us"
	Option		"XkbOptions"	"us"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules/"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "A2"                        # [<bool>]
        #Option     "NoAccel"                   # [<bool>]
        #Option     "HWCursor"                  # [<bool>]
        #Option     "SWCursor"                  # [<bool>]
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "Rotate"                    # [<str>]
        #Option     "UseBIOS"                   # [<bool>]
        #Option     "VideoRAM"                  # <i>
        #Option     "ActiveDevice"              # [<str>]
        #Option     "LCDDualEdge"               # [<bool>]
        #Option     "BusWidth"                  # [<str>]
        #Option     "Center"                    # [<bool>]
        #Option     "PanelSize"                 # [<str>]
        #Option     "TVDotCrawl"                # [<bool>]
        #Option     "TVType"                    # [<str>]
        #Option     "TVOutput"                  # [<str>]
        #Option     "TVVScan"                   # [<str>]
        #Option     "TVHScale"                  # [<str>]
        #Option     "TVEncoder"                 # [<str>]
        #Option     "Refresh"                   # <i>
        #Option     "DisableVQ"                 # [<bool>]
        #Option     "NoDDCValue"                # [<bool>]
        #Option     "Cap0Deinterlace"           # [<str>]
        #Option     "Cap1Deinterlace"           # [<str>]
        #Option     "Cap0FieldSwap"             # [<bool>]
        #Option     "DRIXINERAMA"               # [<bool>]
        Identifier  "Card0"
        Driver      "via"
        VendorName  "Via"
        BoardName   "cle266"
        BusID       "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Samsung"
        ModelName    "LN40A530"
        HorizSync    30.0 - 60.0
        VertRefresh  60.0 - 75.0
EndSection

Section "Module"
        Load  "extmod"
        Load  "dri"
        Load  "dbe"
        Load  "record"
        Load  "xtrap"
        Load  "glx"
        Load  "type1"
        Load  "freetype"
	Load  "vbe"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
	DefaultDepth 16
        SubSection "Display"
                Viewport   0 0
                Depth     16 
		Modes     "1920x1080" "1280x720" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        Screen      0   "Screen0" 0 0
EndSection

```

---

### Post by jamespetts on 2008-05-25
For information, I have just successfully installed the beta drivers for Unichrome on Hardy 8.04, with no install-time errors, following Via's instructions. I am now able to get 1024/768@85hz, whereas before I was only able to get 800x600@60hz. I am using the EX1000G motherboard.

However, 3d screensavers perform poorly. I have not tested any other 3d application. Desktop effects refuse to enable despite using the workaround of whitelisting suggested by the VIA readme document. Video works but is poor in performance, dropping frames and chopping audio. I did not have this problem in Gusty with the Gusty drivers.

Perhaps the final version will be better.

---

### Post by cookiect2003 on 2008-06-17
I get the performance you just described with the openchrome driver, but I'm looking for 3d support so I gave unichrome a shot. I can't even install it on hardy 8.4. some kind of dependancy issue where it tries to delete a huge list of files including gnome and kde.

---

### Post by padlefot on 2008-06-18
I have the same problem as many of you, Installed 8.04 on my girlfriends Laptop with the Via Unichrome PRO card, Is also has a widescreen monitor so I guess I'm extra screwed(F/S AMILO Pro). and I only get 800x600 - I got the 'openchrome' driver working with higher res, but it keeps messing up the colors once in a while - I have to drag the mouse over it to fix it, everything looks really bad. I had to go back to Windows XP (omph) so hopefully Via will release the drivers for Hardy soon! (-:

---

### Post by stalkingwolf on 2008-06-27
I have the same problem, with a twist.
When using the Live CD everything is fine.  Several
options for resolution. all work.

After install 800x600 max.

---

### Post by dkaddict on 2008-07-11
This has been going on for years now with the Via graphics. I have been running Ubuntu since Dapper on an Amilo pro with the Via onboard graphics. I used the Openchrome drivers up until Feisty then had a load of problems when I upgraded to Gutsy so have had to stick with Feisty. I just can't be bothered with all of the messing about editing xorg.conf and that. I get 1280x800 resolution in Fesity with the Openchrome drivers, video works, it is useless at any web site with a lot of ads etc though. My processor maxes out if there are too many smileys on the page. It's a load of rubbish. 3D and Compiz have never worked with the Via cards. Believe me, I have tried. Total waste of time. The cards do not support large bitmaps so can't handle drawing the cube or wobbly windows. I have never seen the 'skip check' option for xorg though so maybe that would get around it. For al the hassle just to get a cube that would probably make this machine scream like a banshee, it ain't worth it. The movements by Via do look promising but by the time they get around to sorting it out, I would have bought a new laptop with nvidia or any graphics card that works properly with Ubuntu. There's no way I would buy another machine with Via graphics. They just do not do Open Source.

DK

---

### Post by zakaria.cse on 2008-07-14
> **whatever69 said:**
> Hopefully this will be good news for us in a month or so as things are still in beta right now.  Keep checking this page:  [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
And this is via's forum specifically related to Linux: [http://www.tkarena.com/forums/linux-arena/](http://www.tkarena.com/forums/linux-arena/)

Got this info after reading this:  [http://www.phoronix.com/scan.php?page=news_item&px=NjQ2Nw](http://www.phoronix.com/scan.php?page=news_item&px=NjQ2Nw)

At last my screen resolution is working perfectly. Here is what I did:
[LIST=1]
[*]Visited "VIA Linux Portal" site: [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
[*]Chose OS as: Ubuntu & Platform as: CN700+VT8237S/VT8237R Plus
[*]Downloaded GFX driver file, extracted it and installed it from terminal.
[/LIST]

Be sure to choose correct platform type for your via graphics device. You will find hardware information by typing following command into terminal:
```
sudo lshw
```

Then search for your correct pci product information, those are listed as "Platform" on "VIA Linux Portal" site.


:guitar:

Thanks a lot!

---

### Post by alliera on 2008-07-14
The driver provided here works for me (EPIA with CX700M2 UniChrome Pro II):

[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

I had to sudo chmod a+r /usr/lib/libGL.so.1.2.via_unichrome or some applications (mplayer, mythtv) would only run as root.

---

### Post by shaunbarlow on 2008-07-22
Thanks for the info guys.
I can now at the least run glxgears on this crazy chipset.
Sadly, Desktop Effects still won't run.
Does anyone have any pointers on getting it all happening?
I installed the "Beta unichrome.83.40692 (2.8M)" from [http://linux.via.com.tw/support/downloadFiles.action]("http://linux.via.com.tw/support/downloadFiles.action")
Was this the right one? (check the bottom of the post for my chipset info)
Do I need to install the item from the source code column as well?

Thanks for bearing with my noob questions. Any help is greatly appreciated.
CHEERS!!!

Here's some info from the terminal, please let me know if there is anything else I should provide:

```
shaun@Monty:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x48 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

```
shaun@Monty:~$ glxgears
2598 frames in 5.0 seconds = 519.510 FPS
2500 frames in 5.0 seconds = 498.909 FPS
2620 frames in 5.0 seconds = 520.689 FPS
2560 frames in 5.0 seconds = 507.463 FPS
2540 frames in 5.0 seconds = 507.956 FPS
2680 frames in 5.0 seconds = 535.745 FPS

```

```
shaun@Monty:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 70)
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)
02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port

```

And here's the bit from sudo lshw relating to the vga
```
     *-pci:0
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci:0
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: UniChrome Pro IGP
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=64 mingnt=2

```

---


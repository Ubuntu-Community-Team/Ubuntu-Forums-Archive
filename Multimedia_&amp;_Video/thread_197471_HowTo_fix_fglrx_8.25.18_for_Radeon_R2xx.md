---
title: "HowTo fix fglrx 8.25.18 for Radeon R2xx"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by Galban on 2006-06-15
After unsuccesfully been trying all kind of wiki's, Ati's official one,  even that one recomended on Ubuntu's 6.06 Guide(method 1 and 2) finally i got 3D acceleration back since upgrading to Dapper on my Radeon 9000pro!! =D> . Here is how. [COLOR="Red"](from a fresh Dapper's install or non yet installed xorg-driver-fglrx)[/COLOR] ;) INFO:This HowTo is a mix of howto's founds on a spanish Ubuntu forum and a SuSe's blog.

NOTE: To know wich kernel are you using:
```
ls /boot/
```

Open a terminal and type this:

1.- sudo apt-get install linux-header-version-of-your-kernel
2.- sudo apt-get install linux-restricted-modules-version-of-your-kernel
3.- sudo apt-get install xorg-driver-fglrx
4.- modprobe agpgart
5.- modprobe -r fglrx
6.- sudo gedit /etc/X11/xorg.conf

add this [COLOR="Red"](in red)[/COLOR] to your graphic card section and SAVE it:

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
Driver "[COLOR="Red"]fglrx[/COLOR]"
BusID "PCI:1:0:0"
[COLOR="Red"]Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "UseInternalAGPGART" "no"[/COLOR]
EndSection

7.- Add this lines to your /etc/modules and SAVE it:
agpgart
fglrx
dri

8.-Make links to your dri modules:
```
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```

9.- Reboot
10.- Go to Ati's Web Site and Download an Old Ati's Installer version like the 8.24.8 (clik on drivers & software and see at the left scroll)
11.- Open a terminal and navigate to where you saved it and type this (in blue):
12.- Extract it : [COLOR="Blue"]sh ati-driver-installer-8.24.8-x86.run --extract /yourHome/someWhere/[/COLOR]
13.- From nautilus find inside of it ( /yourHome/someWhere/extracted )this file [COLOR="Blue"]-->[/COLOR] [COLOR="Blue"]libGL.1.2.so[/COLOR]  and copy/paste it some where you can easily navigate to from your terminal.
14.-Now copy it where it will be founded by fglrx module (in my case was at /usr/lib/. From a terminal type this: [COLOR="Blue"]sudo cp /yourHome/someWhere/extracted/libGL.so.1.2[/COLOR] [COLOR="Blue"]/usr/lib/[/COLOR]

15.-Clean up /usr/lib/ of libGL.so.1.xlibmesa and put atiogl_a_dri.so at right place! I explain....
Put some where else your libGL.so.1.OLD or any other libGL.x.x.so version than that one extracted from the Old Ati's installer, NOT at /usr/lib/. Lets say you can move it to your /home/. Make a copy paste of your libGL.so.1.2 to your /usr/lib/fglrx/ directory too. See if there any remaining libGL.so.1.xlibmesa or any other "libGL.so" than that one extracted from the Old Ati's Installer version, if yes move it to your home, but mainly don't leave it anywhere in your /usr/lib/.../.../ !!
One last thing that I have said here is that I did and maybe it makes it works for me was that I created a directory named "/dri/ " in /usr/lib/ and after a search looking for this file --> atiogl_a_dri.so, after find it, I copy/paste it to /usr/lib/dri/ wich give you this ---> /usr/lib/dri/atiogl_a_dri.so.

[COLOR="Red"]IMPORTATNT NOTE:[/COLOR] if there is the Mesa's version of libGL.so at /usr/lib/, you are gonna get Mesa appearing after fglrxinfo, if there is none, you are gonna get none from fglrxinfo, if there are both it gonna pick the Mesa's one any ways, but if there is one extracted from an old Ati's driver installer version ( 8.24.8 and before) you should get your fglrx-driver to work following the how to. That's all what I did to succesfully get back 3D acceleration. A fresh install and each and one by one of the steps on this HowTo. The proof of what I'm saying about "libGL.x.x.so" is this thread opened by myself couple weeks ago. --> [http://www.ubuntuforums.org/showthread.php?t=184627]("http://www.ubuntuforums.org/showthread.php?t=184627")


It worked for me and now see what fglrxinfo is giving me: :-\" :wink: :lol: \\:D/ 

rodolfo@amdasus:~$ fglrxinfo display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 PRO DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18 )

[COLOR="Red"]IMPORTANT![/COLOR] Make sure that your "fglrx module" is NOT blacklisted from linux-restricted-modules!!

I hope this will help people! GOOD LUCK!! :wink:

---

### Post by Galban on 2006-06-16
I forgot to mention that I'm pretty sure this HowTo should work the same for Radeon's R3XX and R4XX. Any ways, I have to say that I got properly installed (3d acceleration) xorg-driver-fglrx ver. 8.25.18 on a Radeon X1300 fallowing the method 2 on the Unofficial Ati Linux Driver Wiki HOWTO. I f you get fix your API"s error, or your Mesa after fglrxinfo following this proposed HowTo, let me know it.

---

### Post by danoyoto on 2006-06-16
noob question,

how do I go about finding out what my kernel version, restricted-modules, etc. are?

---

### Post by SteinbergerNate on 2006-06-16
It worked. You are awsome. I'm locking my fglrx version in Synaptic right now for a few weeks.

---

### Post by Galban on 2006-06-16
[QUOTE=danoyoto]noob question,

how do I go about finding out what my kernel version, restricted-modules, etc. are?[/QUOTE]

Like this danoyoto:

```
ls /boot/
```

;)

---

### Post by danoyoto on 2006-06-16
I will try tonight when I get home!  thanks.

---

### Post by Galban on 2006-06-16
[QUOTE=SteinbergerNate]It worked. You are awsome. I'm locking my fglrx version in Synaptic right now for a few weeks.[/QUOTE]


SteinbergerNate Trust me bro, I was so frustrated and I don't want just to give up, trying everything, many many hours googleing to find the answer... libGL.1.2.so was the problem. The price was really high, I finished reformating and reinstalling Dapper after the mess from many unsucesfully howto's and only getting API's errors or Mesa showing up after fglrxinfo. This code gave me ligths and guide me to find that answer:

```
LIBGL_DEBUG=verbose glxinfo
```

I'm just so glad to see that this is fixing the problem not only for me! :p

---

### Post by SteinbergerNate on 2006-06-16
Hmmm...Interesting. I just tried to play Paintball2 (the open one based on Quake2) and it still doesn't see the fglrx driver. I get all the API Errors. I did the LIBGL_DEBUG command and I got this: ```
bassmannate@reyn-ubuntu:~/Desktop/paintball2$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 8.25.18 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.25.18 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
display: :0  screen: 0
direct rendering: Yes
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_ATI_element_array,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```
It looks like it's not matching up the version numbers and still thinks that the newer libGL.so should still be there.

---

### Post by Galban on 2006-06-16
SteinbergerNate are you for real still getting API's erros doing fglrxinfo?
About what are you geting from LIBGL_DEBUG=verbose glxinfo it's just ok. I'm getting the same thing. I was just doing reference to that command to say how I found that the right libGL.1.2 was absent on /usr/lib/. It seems to be that atiogl_a_dri.so works together with libGL.X.X.so and needs a version that match. Forget about LIBGL_DEBUG=verbose glxinfo. That was only for reference. Games: I have full 3D acceleration on Enemy Territory and Americas Army. With  fgl_glxgears i'm getting nice fps.

rodolfo@amdasus:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1695 frames in 5.0 seconds = 339.000 FPS
2358 frames in 5.0 seconds = 471.600 FPS
2344 frames in 5.0 seconds = 468.800 FPS
2364 frames in 5.0 seconds = 472.800 FPS
2370 frames in 5.0 seconds = 474.000 FPS
2334 frames in 5.0 seconds = 466.800 FPS
rodolfo@amdasus:~$

---

### Post by SteinbergerNate on 2006-06-16
I don't get API Errors when I run fglrxinfo but when I try to run an openGL game like Paintball2, I get them.

Edit: I also get good FPS when I run glxgears.

---

### Post by Galban on 2006-06-16
[QUOTE=SteinbergerNate]I don't get API Errors when I run fglrxinfo but when I try to run an openGL game like Paintball2, I get them.[/QUOTE]

That's weird,  because you see about 3D games on my Dapper.I don't have Paintball2 but, you never know, it could be the game itself the problem.Before I did this HowTo I did something else about atiogl_a_dri.so. I give you here that link:

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/49900]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/49900")
 
By the way if you are able to do in a terminal  either a "fgl_glxgears" or "glxgears -printfps", that's gonna be a proof that your Ati xorg-driver-fglrx is well installed and working properly and the problem it's Paintball2 itself!  ;)

---

### Post by edJquarK on 2006-06-18
I read in a forum that there was a problem with the new ati drivers and that installing an old one would solve it, but i didn't know how to do it as i have xorg7.0 and was not supported. So, thanks for your HowTo.

Now, looking for a solution i installed the new drivers wich i downloaded from the ATI support page, and compiling the driver from /lib/modules/fglrx/ now i receive in Xorg.0.log that acceleration is enabled. The only problem is that i can't start X!!

/var/log/Xorg.0.log

```
(II) fglrx(0):     Version: 8.25.18
(II) fglrx(0):     Date: May 18 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.15-25-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [pcie] 65536 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x40000000 FBMappedSize: 0x00715000
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,1261)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		22 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete

```

I don't know what to do now. I tried both replacing "ati" for "fglrx" in xorg.conf and running aticonfig --initial,  none of them worked.

If you need it to help me solve the problem i can post my xorg.conf and everything. Thanks again.

---

### Post by edJquarK on 2006-06-18
Another info that may be important and have just discovered.

In Xorg.0.log

```
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

```

And continues like this until drmOpenDevice: node name is /dev/dri/card254.

What does this mean?

---

### Post by Galban on 2006-06-18
Sounds like your xorg.conf it's a mess.That's what aticonfig --initial (ver 8.25.18 ) does, always a big mess in xorg.conf.Let's see. Try this:

Start your PC, at the GRUB count-down press ESCAPE, then choose safe mode. After everythings loads and the $ symbol appears type the xorg.conf command:

```
sudo dpkg-reconfigure xserver-xorg
```

Now choose the VESA driver, then after give to all the default answer. Reboot.

Follow as described in this "howto" each step and this aditional command just before rebooting:

```
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```

Don't forget follow steps as it appears here. I hope this is gonna work for you. ;)

---

### Post by edJquarK on 2006-06-18
OK, there's no need to use Vesa, i can boot perfectly with "ati" driver and the backup of the original xorg.conf.

I'm going to do what you suggest, i'll uninstall the fglrx driver and start again following your HowTo, but that will be tomorrow. Thanks.

---

### Post by edJquarK on 2006-06-19
Well, it was not necessary to uninstall anything because i got my problem solved. I have an ATI radeon xpress 200M, and it seems that to use 3d acceleration it needs 128mb of shared memory.

So i simply went to the bios and changed the video memory from "sideport" to "sideport + UMA" and gave  128mb to the shared memory, 256mb total. That way it boots smoothly. Now the only problem is that, as i have read, the new driver doesn't work properly with my card, the windows doesn't appear and things like that. Let's see if i can solve it, i'll try replacing the libGL from an older driver just in case...

---

### Post by rhipwell on 2006-06-19
No dice, still getting 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
when i run fglrxinfo. 

I'm configuring via ssh ( working remotly right now ) and my wife is there to physically log into gnome for me. Please let me know if you have any ideas. Thanks

---

### Post by edJquarK on 2006-06-19
[QUOTE=rhipwell]No dice, still getting 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
when i run fglrxinfo. [/QUOTE]

I tried following the HowTo from a clean install and i get Mesa GLX Indirect as well, any other suggestion? I think i will wait for the next ATI drivers hoping they solve the problem with my card, here's an screenshot: 

[IMG]http://edjquark.ed.funpic.de/images/instantanea1.png[/IMG]

---

### Post by praetor_alpha on 2006-06-19
wow, thanks.
(AMD Athlon XP 2500+, 1 gig PC3200, Radeon 9600 XT 128 MB)
alpha@alpha-engine:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2994 frames in 5.0 seconds = 598.800 FPS
3163 frames in 5.0 seconds = 632.600 FPS
3155 frames in 5.0 seconds = 631.000 FPS
3150 frames in 5.0 seconds = 630.000 FPS
3155 frames in 5.0 seconds = 631.000 FPS
3162 frames in 5.0 seconds = 632.400 FPS
3155 frames in 5.0 seconds = 631.000 FPS
3065 frames in 5.0 seconds = 613.000 FPS

---

### Post by Galban on 2006-06-19
[QUOTE=edJquarK]I tried following the HowTo from a clean install and i get Mesa GLX Indirect as well, any other suggestion? I think i will wait for the next ATI drivers hoping they solve the problem with my card, here's an screenshot: 

[IMG]http://edjquark.ed.funpic.de/images/instantanea1.png[/IMG][/QUOTE]

Bro! I dont know where and what are you reading. In your Terminal cosole, I can perfectly read that it says Ati Technologies Inc. It's clearly says you have your fglrx up and working. #-o

---

### Post by Galban on 2006-06-19
[QUOTE=rhipwell]No dice, still getting 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
when i run fglrxinfo. 

I'm configuring via ssh ( working remotly right now ) and my wife is there to physically log into gnome for me. Please let me know if you have any ideas. Thanks[/QUOTE]


Ok, go to /usr/lib/ and look for file that looks like "libGL.so.1.xlibmesa" . As root at properties change the name of it (.old ) or better yet move it to your home as a backup. Now start from step #10 (lazy way). Better yet, after you move libGL.so.1.xlibmesa to your home (or your Trash :lol:  ) , start over from step 1 :!: (making sure way )

[COLOR="Red"]WARNING[/COLOR]: as I have said this HowTo works only if you do it from a fresh install or at worst, with "xorg-driver-fglrx" [COLOR="Red"][COLOR="Red"]NOT[/COLOR][/COLOR] instaled!!

---

### Post by rhipwell on 2006-06-20
gave that a whirl and now i'm getting API errors](*,)  I think I'll do a fresh install later tonight when I have a chance to play. I'll let you know how it goes.

---

### Post by elpresidente on 2006-06-20
Was hopeful for this tutorial to work as I have tried several others. When I reboot xserver does not start.

lsmod | grep fglrx returns nothing
dmesg | grep fglrx returns nothing

From Xorg.0.log:
```
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined Device "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]" referenced by Screen "Default Screen".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor

```

and from xorg.conf:
```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver "fglrx"
	BusID "PCI:1:0:0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "UseInternalAGPGART" "no"
EndSection

```

Where do I go from here?

---

### Post by elpresidente on 2006-06-20
[QUOTE=elpresidente]Was hopeful for this tutorial to work as I have tried several others. When I reboot xserver does not start.

lsmod | grep fglrx returns nothing
dmesg | grep fglrx returns nothing

From Xorg.0.log:
```
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined Device "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]" referenced by Screen "Default Screen".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor

```

and from xorg.conf:
```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver "fglrx"
	BusID "PCI:1:0:0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "UseInternalAGPGART" "no"
EndSection

```

Where do I go from here?[/QUOTE]

Alright, that was dumb. I had just copied and paste the whole section device including model from this tutorial. I changed it but and still getting mesa driver instead of fglrx.

I am completely stumped. Still nothing from dmesg or lsmod.

---

### Post by tommohawk on 2006-06-20
Please help - I have tried a fresh install, had it working perfectly until recent updates.   I thought I had this issue solved about 6 weeks ago whilst I was still using Dapper Beta but I am banging my head against the wall.

This is what I have:

fglrxinfo Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

It is the unfortunate RadeonXpress 200M card and I really hate it but its part of the laptop so I have no choice.

Any ideas how to solve the XFree86-DRI error above - I am stuck!

---

### Post by Galban on 2006-06-20
Let's try to make understand this for the last time ](*,)  #-o : if there is the Mesa's version of libGL.so at /usr/lib/, you are gonna get Mesa appearing after fglrxinfo, if there is none, you are gonna get none from fglrxinfo, if there are both it gonna pick the Mesa's one any ways, but if there is one extracted from an old Ati's driver installer version ( 8.24.8 and before) you should get your fglrx-driver to work following the how to. That's all what I did to succesfully get back 3D acceleration. A fresh install and each and one by one of the steps on this HowTo. The proof of what I'm saying about "[COLOR="Blue"]libGL.x.x.so[/COLOR]" is this thread opened by myself couple weeks ago. I'm copying pasting here what it says. Any ways here is the link:  [http://www.ubuntuforums.org/showthread.php?t=184627]("http://www.ubuntuforums.org/showthread.php?t=184627")

---------------------------------------------------------------------------

[COLOR="Navy"]Synaptic, apt-get, paralized by a broken xorg-driver-fglrx package[/COLOR]

After doing an upgrade to kernel 2.6.15-23-x86 (I have a AMD Athlon 1400 procesor and an Ati Radeon 9000 pro) I saw there was an upgrade for the Ati propietary driver to version 8.25.18-x86 too. I fallowed the method 2 on the Unofficial Ati Linux Driver Wiki HOWTO as always I did before in order to get succesfully the Ati propietary driver working. But, this time I was always getting Mesa on my fglrxinfo output and not Ati as it used to be before. With Mesa I didnt get 3D acceleration as I used to get with Ati. So then, I tryed some other ways, and finished for meestup my xorg.conf wich I have to reconfigure to get back Xwindow. I keep tryng many others things as for example the ATi&#347; owns HowTo install, and the product of all of that is that i´m now using the k7 version of 2.6.15-23 kernel, a bigger and desorganized xorg.conf, and an APT-GET paralized by a broken xorg-driver-fglrx. I can´t install or uninstall nothing. Here is the common output of my apt-get:

[COLOR="Red"]Now watch what is marked in red!!! --->[/COLOR]


```
root@amdasus:/# sudo apt-get install xorg-driver-fglrx Reading package lists... Done
Building dependency tree... Done
xorg-driver-fglrx is already the newest version.
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 59 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 26.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 204785 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/[COLOR="Red"]usr/lib/libGL.so.1[/COLOR]' with
  different file `/usr/lib/fglrx/[COLOR="Red"]libGL.so.1.xlibmesa[/COLOR]', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@amdasus:/#
```

Ok, now that it's clear (I hope), I have to say If you my dears friends, if you aren't getting possitive results even after follow this HowTo (lets say HowIdid instead :lol: ) I'm really sorry to say, I dont know why!! :roll:

Once again I have expalined here how to get rip of the Mesa version of libGL see at RE #21 in this same thread!

---

### Post by Dzo on 2006-06-21
Having similar problems with it still showing up as MESSA.

```
 
iang@LNXFNK01:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

```

iang@LNXFNK01:~$ glxinfo
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
    GL_ARB_multitexture, GL_ARB_imaging, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

```



```

iang@LNXFNK01:~$ dmesg | grep fglrx
[17179591.872000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179591.872000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179591.872000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179605.184000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[17179605.184000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[17179605.192000] [fglrx] total      GART = 134217728
[17179605.192000] [fglrx] free       GART = 118222848
[17179605.192000] [fglrx] max single GART = 118222848
[17179605.192000] [fglrx] total      LFB  = 28307456
[17179605.192000] [fglrx] free       LFB  = 22016000
[17179605.192000] [fglrx] max single LFB  = 22016000
[17179605.192000] [fglrx] total      Inv  = 0
[17179605.192000] [fglrx] free       Inv  = 0
[17179605.192000] [fglrx] max single Inv  = 0
[17179605.192000] [fglrx] total      TIM  = 0

```

Output of 'dmesg | grep fglrx' is above which shows its loading alright??!? I'm really confussed. fgl_glxgears does the following..........

```

iang@LNXFNK01:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  33
  Current serial number in output stream:  33

```

It's a fresh install so it should be alright i followed the HowTo word for word!

edit : I have a Radeon Mobile 9000 (Which is the R250 chipset)

edit 2: Contents of my /usr/lib here if that helps also......

```

iang@LNXFNK01:~$ ls -l /usr/lib/libGL*
lrwxrwxrwx 1 root root     16 2006-06-20 20:42 /usr/lib/libGLEW.so.1.3 -> libGLEW.so.1.3.1
-rw-r--r-- 1 root root 205204 2005-11-30 20:47 /usr/lib/libGLEW.so.1.3.1
-rwxr-xr-x 1 root root 727430 2006-06-21 12:44 /usr/lib/libGL.so.1
-rwxr-xr-x 1 iang iang 727430 2006-04-11 21:59 /usr/lib/libGL.so.1.2
lrwxrwxrwx 1 root root     20 2006-06-20 20:42 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.060401
-rw-r--r-- 1 root root 479244 2006-05-05 16:05 /usr/lib/libGLU.so.1.3.060401

```


edit edit edit ;) : I didn't have a libGL.so.1.xlibmesa only a libGL.so.1 i've renamed this, moved it, messed around with it to no avail! Any guidance would be great!

---

### Post by Galban on 2006-06-21
OK Dzo, put some where else your libGL.so.1.OLD, NOT at /usr/lib/. Lets say you can move it to your /home/. Make a copy paste of your libGL.so.1.2 to your /usr/lib/fglrx/ directory too. See if there any remaining libGL.so.1.xlibmesa or any other "libGL.so" than that one extracted from the Old Ati's Installer version, if yes move it to your home, but mainly don't leave it anywhere in your /usr/lib/.../.../ !! 
One last thing that I have said here is that I did and maybe it makes it works for me was that I  created a directory named "/dri/ " in /usr/lib/ and after a search looking for this file --> atiogl_a_dri.so, after find it, I copy/paste it to /usr/lib/dri/ wich give you this --->  /usr/lib/dri/atiogl_a_dri.so. I didn't nothingelse than that and this how to , I atswer it.

I just hope this gonna work for you and everybody else!

EDIT Dzo look what I get doing  ls -l /usr/lib/libGL*

```
rodolfo@amdasus:~$ ls -l /usr/lib/libGL*
lrwxrwxrwx 1 root root     16 2006-06-15 01:59 /usr/lib/libGLEW.so.1.3 -> libGLEW.so.1.3.1
-rw-r--r-- 1 root root 205204 2005-11-30 15:47 /usr/lib/libGLEW.so.1.3.1
lrwxrwxrwx 1 root root     12 2006-06-15 17:18 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 773890 2006-06-15 18:22 /usr/lib/libGL.so.1.2
lrwxrwxrwx 1 root root     20 2006-06-15 01:59 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.060401
-rw-r--r-- 1 root root 479244 2006-05-05 11:05 /usr/lib/libGLU.so.1.3.060401
rodolfo@amdasus:~$

```

---

### Post by Dzo on 2006-06-21
You da man !!!! :D

Sorted, there were some of the libGL.so.1.xlibmesa files in /usr/lib/fglrx/, moved them to home, thats now all sorted.

The 2nd thing was that when doing LIBGL_DEBUG=verbose glxinfo i found as you suggested that atiogl_a_dri.so was in the wrong location it was looking for it in /usr/X11R6/lib/modules/dri/ so i made that directory, copied the file and woohoo its now going :)

Galban you're a :KS


EDIT : One more question! How can i now stop these files being updated so i don't have to go through all of this again?!

---

### Post by Galban on 2006-06-21
[QUOTE=Dzo]You da man !!!! :D

Sorted, there were some of the libGL.so.1.xlibmesa files in /usr/lib/fglrx/, moved them to home, thats now all sorted.

The 2nd thing was that when doing LIBGL_DEBUG=verbose glxinfo i found as you suggested that atiogl_a_dri.so was in the wrong location it was looking for it in /usr/X11R6/lib/modules/dri/ so i made that directory, copied the file and woohoo its now going :)

Galban you're a :KS


EDIT : One more question! How can i now stop these files being updated so i don't have to go through all of this again?![/QUOTE]

Ok Dzo to blok fglrx to be updated open Synaptic, search for fglrx. Left click on xorg-driver-fglrx just to mark it, then on the Package Menu make chek up on "Lock Version". Same thing for fglrx-control and all other already installed fglrx's related package. Ok bro glad to konw that it's working for you now! :D

---

### Post by edJquarK on 2006-06-21
[QUOTE=Galban]Bro! I dont know where and what are you reading. In your Terminal cosole, I can perfectly read that it says Ati Technologies Inc. It's clearly says you have your fglrx up and working. #-o[/QUOTE]

Yeah i know it's up, but it's not working correctly, that's why i captured the screen with the console saying it was everything as supposed but the result was not. You may haven't noticed the tray with doubled and moved icons, and the window itself and it happens the same with everything, objects in front of others when they shouldn't and things like that. That's the point, fglrx is working but there's a problem with my card that has to be solved. Thanks anyway.

---

### Post by edJquarK on 2006-06-21
[QUOTE=tommohawk]Please help - I have tried a fresh install, had it working perfectly until recent updates.   I thought I had this issue solved about 6 weeks ago whilst I was still using Dapper Beta but I am banging my head against the wall.

This is what I have:

fglrxinfo Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

It is the unfortunate RadeonXpress 200M card and I really hate it but its part of the laptop so I have no choice.

Any ideas how to solve the XFree86-DRI error above - I am stuck![/QUOTE]

Hey! i've just read you have the ATI radeon xpress 200M as well. With the old drivers i got it running too, but with the new version compatible with xorg7 there's no way.

I got it to show that the driver was running and everythig was ok but you can see a screenshot in another post in this thread. A question, if you do
```

lsmod | grep fglrx
```
It shows you anything? Because i got a probem with the module not being loaded.

Galvan, a question for you, how can i know if fglrx module is blacklisted from linux-restricted-modules?? and if so, how can i unblacklist it?

---

### Post by tommohawk on 2006-06-21
[QUOTE=edJquarK]Hey! i've just read you have the ATI radeon xpress 200M as well. With the old drivers i got it running too, but with the new version compatible with xorg7 there's no way.

I got it to show that the driver was running and everythig was ok but you can see a screenshot in another post in this thread. A question, if you do
```

lsmod | grep fglrx
```
It shows you anything? Because i got a probem with the module not being loaded.

Galvan, a question for you, how can i know if fglrx module is blacklisted from linux-restricted-modules?? and if so, how can i unblacklist it?[/QUOTE]

Right, a few things here then.  Firstly, I now have perfect(?) 3D accel using my xpress 200M card - which is no small feat believe me.

Secondly, the output you asked for:

```
lsmod | grep fglrx
fglrx                 471136  7
agpgart                34888  2 fglrx,ati_agp

```

Thirdly, blacklisting (or not) you need to look at /etc/default/linux-restricted-modules-common and see if the FGLRX module is blacklisted.  I have mine blacklisted and my system works fine.

Now then, for anyone else reading this post....

There are various HOWTOs on the ATI issues and I believe that the xpress 200M card is one of the more problematic ones that ATI produce (certainly with the new 8.25.18 drivers).  I got it to work by doing the following...

1.   Clean Dapper Install.
2.   Upgrade and update everything.
3.   Download the 8.24.8 drivers from the ATI website.
4.   Build the ubuntu packages from these drivers.
5.   Recompile the Kernel.
6.   Extract the libGL.so.1.2 driver from the ATI package you downloaded in step 3.
7.   Replace the libGL.so.1.2 file in /usr/lib
8.   Remove and *mesa* files from /xorg/fglrx and place the libGL.so.1.2 file in that directory also.
9.   Configure your xorg.conf file in accordance with previous posts in this thread.
10. Blacklist the fglrx driver as detailed above.
11.  Reboot and all should work.

I more or less used these [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) instructions and substituted 8.25.18 for 8.24.8 and it all worked (must use method 2).

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)

```

```
 fgl_glxgears
Using GLX_SGIX_pbuffer
1016 frames in 5.0 seconds = 203.200 FPS
2135 frames in 5.0 seconds = 427.000 FPS
2467 frames in 5.0 seconds = 493.400 FPS
1850 frames in 5.0 seconds = 370.000 FPS
2145 frames in 5.0 seconds = 429.000 FPS
3817 frames in 5.0 seconds = 763.400 FPS
3806 frames in 5.0 seconds = 761.200 FPS
3813 frames in 5.0 seconds = 762.600 FPS
3631 frames in 5.0 seconds = 726.200 FPS

```

Hope that helps someone!

Thanks to everyone who has contributed to all the "fix ATI problem" type posts i this and other threads.;)

---

### Post by edJquarK on 2006-06-21
Incredible **tommohawk**, i'll bookmark your post right now ;) and when i finish exams i'll try your method, sounds ok.

If you install the 8.24.8 driver, it works with xorg7? Or how did you do it exactly? And recompiling the kernel... without changing anything? Just make and make install? It's a long time since i don't compile a kernel :confused: 

A useful post for me anyway, there's a light at the end of the tunnel!!

---

### Post by tommohawk on 2006-06-21
[QUOTE=edJquarK]
If you install the 8.24.8 driver, it works with xorg7? Or how did you do it exactly? And recompiling the kernel... without changing anything? Just make and make install? [/QUOTE]
Yeah, I might have got carried away when typing!  Obviously you need to install the packages you built from the 8.24.8 drivers before you recompile.

The instructions in the link above are fairly clear and yes it works with Xorg 7O:)

---

### Post by Galban on 2006-06-21
[QUOTE=edJquarK]Hey! i've just read you have the ATI radeon xpress 200M as well. With the old drivers i got it running too, but with the new version compatible with xorg7 there's no way.

I got it to show that the driver was running and everythig was ok but you can see a screenshot in another post in this thread. A question, if you do
```

lsmod | grep fglrx
```
It shows you anything? Because i got a probem with the module not being loaded.

[COLOR="Red"]Galvan, a question for you, how can i know if fglrx module is blacklisted from linux-restricted-modules?? and if so, how can i unblacklist [/COLOR]it?[/QUOTE]


Like this edJquarK:

```
sudo gedit /etc/default/linux-restricted-modules-common
```

If it's appears fglrx en betwin those "  "  it's because it is blacklisted. You can disable any module from "restricted" right here, editing it.

---

### Post by Galban on 2006-06-21
[QUOTE=edJquarK]Yeah i know it's up, but it's not working correctly, that's why i captured the screen with the console saying it was everything as supposed but the result was not. You may haven't noticed the tray with doubled and moved icons, and the window itself and it happens the same with everything, objects in front of others when they shouldn't and things like that. That's the point, fglrx is working but there's a problem with my card that has to be solved. Thanks anyway.[/QUOTE]

Listen, i'm not pretending to do affirmations just from no where, but in my opinion looks like your problems are about your desktop enviroment, wich is 
KDE. Am I wrong? Could be. In my case with Gnome everything about graphics it's good, 8)

---

### Post by edJquarK on 2006-06-22
[QUOTE=Galban]Listen, i'm not pretending to do affirmations just from no where, but in my opinion looks like your problems are about your desktop enviroment, wich is 
KDE. Am I wrong? Could be. In my case with Gnome everything about graphics it's good, 8)[/QUOTE]

It's not a bad opinion, you're completely right. Because this is what Xorg.0.log shows now:
```
(WW) fglrx(0): Specified desktop setup not supported: 8
```
But with "ati" driver i have no issues at all. Maybe with gnome it works better, i'm gonna try installing it right now. If it persists i'll follow **tommohawk** instructions.

---

### Post by Knight on 2006-06-22
I've been trying for 2 days now (](*,) ) and still can't get my xpress 200M working right. Everytime I try to run fglrxinfo I get:
```
Error: couldn't find RGB GLX visual!
```
When I try to do fgl_glxgears I get:
```
Using GLX_SGIX_pbuffer
Error: couldn't get an RGBA, Double-buffered visual
```
I'm pretty new to ubuntu, but thought I was following the directions here pretty well, apparently I missed something. Any insight would be helpful.

---

### Post by edJquarK on 2006-06-22
I have to thank all the people who helps in this forum, and specially **Galban ** and **tommohawk** because i finally had 3d acceleration running with my Radeon Xpress 200M. 

I followed tommohawk instructions and everything is running smoothly.

> I've been trying for 2 days now ( ) and still can't get my xpress 200M working right.

You may as well do what tommohawk posted, gives no problems.

Thanks again.

---

### Post by Knight on 2006-06-22
[QUOTE=edJquarK]You may as well do what tommohawk posted, gives no problems.[/QUOTE]
I did try as he posted, in fact I tried it multiple consecutive times. I should also mention I'm on a 64bit laptop running the 64bit version of Ubuntu.

---

### Post by tommohawk on 2006-06-22
[QUOTE=Knight]I did try as he posted, in fact I tried it multiple consecutive times. I should also mention I'm on a 64bit laptop running the 64bit version of Ubuntu.[/QUOTE]

Well there you have it - that's the problem.  For the time being, i wouldn't even bother with the 64-bit version until it is more widely suppported.

My advice is to stick with the 32-bit install - I am not sure how much benefit the 64-bit gives you anyway.

By the way - what laptop is it?

---

### Post by Knight on 2006-06-22
[QUOTE=tommohawk]By the way - what laptop is it?[/QUOTE]

it's a [Fujitsu Siemens Amilo A1650G]("http://www.comparestoreprices.co.uk/laptops/fujitsu-siemens-amilo-a1650.asp")
And yeah, after all these annoyances with setting up a well working 64bit enviroment, like having to do a chroot to make firefox plugins work, and wine complications, and now this with the ATI card, clearing out and just putting on the 32bit version of Ubuntu might be a real option...

---

### Post by edJquarK on 2006-06-22
[QUOTE=Knight]I did try as he posted, in fact I tried it multiple consecutive times. I should also mention I'm on a 64bit laptop running the 64bit version of Ubuntu.[/QUOTE]

I also have a 64bit processor but i use the 32 version. My laptop had windows xp (32bit) preinstalled, and when i bought it it already existed the 64 version, so if HP neither use nor support the 64 version they must have a reason, and actually there are not such compatibility with wireless and graphics for 64 based systems.

I first tried with x_64 distributions and i couldn't have anything working, so i decided to wait until drivers and compatibility are improved.

---

### Post by tommohawk on 2006-06-22
[QUOTE=Knight]it's a [Fujitsu Siemens Amilo A1650G]("http://www.comparestoreprices.co.uk/laptops/fujitsu-siemens-amilo-a1650.asp")
And yeah, after all these annoyances with setting up a well working 64bit enviroment, like having to do a chroot to make firefox plugins work, and wine complications, and now this with the ATI card, clearing out and just putting on the 32bit version of Ubuntu might be a real option...[/QUOTE]

I would highly recommend that you stick with the 32-bit for now.  I have an HP dv8000 laptop with a Turion64 processor and all ATI chipset including the xpress 200M card.  I have had no end of problems with Linux on this machine and have tried almost every distro there is.

IMHO there is only one choice and that is Ubuntu 6.06 32-bit using the GNOME environment.  Don't waste your time with Kubuntu, if you want to use KDE then install it as a package after.  For some reason Ubuntu correctly detects and configures all my hardware (including internal card reader, infra red remote control, volume keys etc) Kubuntu does not configure everything and always gave me no end of problems.

Hope that helps - post back if you need any further help.

---

### Post by edJquarK on 2006-06-22
[QUOTE=tommohawk]I would highly recommend that you stick with the 32-bit for now.  I have an HP dv8000 laptop with a Turion64 processor and all ATI chipset including the xpress 200M card.  I have had no end of problems with Linux on this machine and have tried almost every distro there is.

IMHO there is only one choice and that is Ubuntu 6.06 32-bit using the GNOME environment.  Don't waste your time with Kubuntu, if you want to use KDE then install it as a package after.  For some reason Ubuntu correctly detects and configures all my hardware (including internal card reader, infra red remote control, volume keys etc) Kubuntu does not configure everything and always gave me no end of problems.

Hope that helps - post back if you need any further help.[/QUOTE]

Hey! same laptop as me!! and... i use Kubuntu!! i haven't tried with Ubuntu, but it's true that volume keys, and card reader don't work, you have them working and detected during installation?? What a surprise. This post is being even more useful than what i thought. 

Before Ubuntu 6.06 LTS was released i used Mandriva 2006 Powerpack because it was the only that run decently, graphics and networking mainly. Then i switched to Kubuntu Dapper and now I'm gonna go with Ubuntu. Thank you very much **tommohawk**, i got 3D and now i can have a fully functional installation.

Just one question, you have wireless running with native drivers or ndiswrapper?? I use ndiswrapper as bcm43xx says i have the card and scans for networks, but when trying to connect never receives dhcpoffers and never connects. Thanks again, it's great you have same laptop as me, you solved tons of problems.

---

### Post by tommohawk on 2006-06-23
[QUOTE=edJquarK]
Just one question, you have wireless running with native drivers or ndiswrapper?? I use ndiswrapper as bcm43xx says i have the card and scans for networks, but when trying to connect never receives dhcpoffers and never connects. Thanks again, it's great you have same laptop as me, you solved tons of problems.[/QUOTE]

Ndiswrapper - there are still stability issues with the kernel drivers so I have blacklisted bcm43xx in /etc/modprobe.d and use ndiswrapper instead.  It doesn't cause me any problems. 

Have now managed to get Xgl working too - now I know why people kept going on about it - I was blown away!

---

### Post by rekahsoft on 2006-06-25
Ok...i have been strugling with this issue for at least 2 weeks...I have the compaq R4000 series laptop with the Radeon 200M...i just cannot get fglrx working...check [this]("http://ubuntuforums.org/showthread.php?t=199421&page=3") for the problem/s i am getting. Thanks for the help :)

---

### Post by tommohawk on 2006-06-25
[QUOTE=rekahsoft]Ok...i have been strugling with this issue for at least 2 weeks...I have the compaq R4000 series laptop with the Radeon 200M...i just cannot get fglrx working...check [this]("http://ubuntuforums.org/showthread.php?t=199421&page=3") for the problem/s i am getting. Thanks for the help :)[/QUOTE]
OK, first thing is to stay calm - I have read your other posts on the thread you linked to and can see that you are more than a little frustrated;) 

I have been there, believe me - I had full 3D accel working until about 2-3 weeks ago when the new 8.25.18 drivers were released - the system did an upgrade and broke my drivers.  Now seeing as I had been using Dapper since early Beta days, I was a little hacked off as my system was nicely configured etc.....

Anyway, read back in this thread and look at what I did to get this working.  It worked for me and I haven't had anyone say that it hasn't worked for the other people that have followed it.

When the guide talks about recompiling the kernel, what I mean is that you install the .deb packages and then recompile.  Use the links in the post and follow the install guide.  The install guide works, its just that you have to substitute all references to 8.25.18 with 8.24.8.  Try it again, have faith and it will work - any problems post back and I will try to help.

---

### Post by bendi on 2006-06-25
Hi, I'am using Slackware, but I found this topic very helpful. Still I have some problems: DRI module won't load and this causes Mesa drivers tu load instead of ATI's. In X.org log I found such warnings:
```
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```
and little bit later:
```
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
```
Then running for example fgl_glxgears or even fglrxinfo return an error:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
```

Now I'm more willing to believe that it's due to the lack of DRI module (I don't have any at all... "modprobe dri" returns an error of missing module). However, I was pretty sure that DRM support and DRI module for radeon from kernel aren't needed to run ATI drivers, I also read that DRI from kernel should be disabled and that ATI drivers build their own DRI module. But it seems that it was a piece of nonsense. So could you tell me if kernel DRI support is necessary tu run these drivers?

I'am using kernel 2.6.17.1, drivers installed by *ati-driver-installer-8.25.18-x86.run* and libGL.so from *ati-driver-installer-8.24.8-x86.run* as it was said in this HowTo. GFX card is ATI Radeon 9100.

---

### Post by rekahsoft on 2006-06-25
Ok...i have done everything now and am getting the following error when i try fglrxinfo:
```
collin@RekahSoft:~$ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

``` When i put back libGL.so.1 and try fglrxinfo i get the Mesa drivers...what did i do wrong? This is what i get from dmesg | grep fglrx:
```
collin@RekahSoft:~/build/extract$ dmesg | grep fglrx
[17179619.092000] [fglrx] Maximum main memory to use for locked dma buffers: 314 MBytes.
[17179619.092000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0[17179619.160000] [fglrx:firegl_pci_getinfo] *ERROR* Cannot find Asic ID: 0x0001[17179619.160000] [fglrx:firegl_init_asic] *ERROR* Cannot get PCI info.
[17179620.780000] [fglrx:firegl_unlock] *ERROR* Process 4446 using kernel context 0
```. This is what i get from lsmod | grep fglrx:
```
collin@RekahSoft:~/build/extract$ lsmod | grep fglrx
fglrx                 388908  0
agpgart                34888  2 fglrx,ati_agp
```.Thanks for the help.

---

### Post by edJquarK on 2006-06-25
If you have problems with libGL.so.1 check this:

[http://www.thinkwiki.org/wiki/Problems_with_fglrx#Softlink_hell](http://www.thinkwiki.org/wiki/Problems_with_fglrx#Softlink_hell)

and by the way, you're still loading 8.25.18, but you may get it working.

---

### Post by kcallis on 2006-06-25
[QUOTE=tommohawk]I would highly recommend that you stick with the 32-bit for now.  I have an HP dv8000 laptop with a Turion64 processor and all ATI chipset including the xpress 200M card.  I have had no end of problems with Linux on this machine and have tried almost every distro there is.

IMHO there is only one choice and that is Ubuntu 6.06 32-bit using the GNOME environment.  Don't waste your time with Kubuntu, if you want to use KDE then install it as a package after.  For some reason Ubuntu correctly detects and configures all my hardware (including internal card reader, infra red remote control, volume keys etc) Kubuntu does not configure everything and always gave me no end of problems.

Hope that helps - post back if you need any further help.[/QUOTE]

I am using the same machine as well... Although everything seems for the most part, the biggest issue I am having is being able to properly work with the mouse. I have a hard time highlight and moving windows... Has anyone run into that problem... Any solution would be greatly appreciated!

---

### Post by rekahsoft on 2006-06-25
Ok..i will try the link you gave me...> by the way, you're still loading 8.25.18, but you may get it workin. This is impossable...take a look at the screenshot...man this is wierd.

Edit: I just said what the link said and the one command "ls -la *GL*" does not work...it says:```
ls: *GL*: No such file or directory
```...so what am i doing wrong?

---

### Post by edJquarK on 2006-06-26
The link i gave you was for Debian.

You have to run the command "ls -la *GL*" in the /usr/lib folder, not in /usr/X11R6/lib, and you'll see the softlinks. But i think this is a minor problem for you.

Synaptic says you have 8.24.8, but Xorg log says it loads 8.25.18, the problem is in there, but i don't know how to solve it, cause i'm sure you've installed it from a fresh install, which should not give such problems. I'm not a linux expert, if there's one following this thread and have an idea... everything's welcomed.

Edit: i've just read **almahtar** post [here]("http://www.ubuntuforums.org/showthread.php?p=1182252#post1182252"). If you're not too tired and fed up, you can try once more from "scratch" as mentioned.

---

### Post by rekahsoft on 2006-06-26
Ok...i will give it a try and report back in a little :)

Edit: I am going to make a clean install once again...will somebody give me detailed step by step instrucions so i can get this working once and for all. Thanks.

---

### Post by tommohawk on 2006-06-26
[QUOTE=rekahsoft]Ok...i will give it a try and report back in a little :)

Edit: I am going to make a clean install once again...will somebody give me detailed step by step instrucions so i can get this working once and for all. Thanks.[/QUOTE]

Man, I don't know what to say to you.  I did it exactly as I said earlier in this thread and it worked perfectly for me.  I can't understand why you are having this problem.

Are you installing the .deb packages through the command line and following the wiki article step by step?

It will only work on a clean install - can't understand why you are having so much trouble.

---

### Post by tommohawk on 2006-06-26
OK this might be useful.  Just found this thread on the Ubuntu forums...

[http://www.ubuntuforums.org/showthread.php?t=204109](http://www.ubuntuforums.org/showthread.php?t=204109)

It has a link for the new release of the ATI driver version 8.26.18

I have no idea if it works or not but hey, if you are having so many problems it might be worth a shot.

I am not going to try it because mine is working!  If someone else is brave enough to try it on their x200M card then please let us all know if it works!

By the way - for those who have not noticed - the new drivers are in the Dapper repositories - try at your own risk!!

---

### Post by rekahsoft on 2006-06-27
I will try it tonight...i report my findings ASAP :)

---

### Post by jhr79 on 2006-06-28
[QUOTE=tommohawk]OK this might be useful.  Just found this thread on the Ubuntu forums...

[http://www.ubuntuforums.org/showthread.php?t=204109](http://www.ubuntuforums.org/showthread.php?t=204109)

It has a link for the new release of the ATI driver version 8.26.18

I have no idea if it works or not but hey, if you are having so many problems it might be worth a shot.

I am not going to try it because mine is working!  If someone else is brave enough to try it on their x200M card then please let us all know if it works!
[/QUOTE]

BTW: New driver doesn't fix problems with x200M cards according to the post #7 on that thread.

---

### Post by tommohawk on 2006-06-28
[QUOTE=jhr79]BTW: New driver doesn't fix problems with x200M cards according to the post #7 on that thread.[/QUOTE]

Curious.... because acording to this thread..... it does :-? 

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

I would like to see somebody elses results with this card and driver before I upgrade mine ;-)

---

### Post by jhr79 on 2006-06-28
[QUOTE=tommohawk]Curious.... because acording to this thread..... it does :-? 

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

I would like to see somebody elses results with this card and driver before I upgrade mine ;-)[/QUOTE]

I will try this instantly after workday :cool: Let's see what happens...

---

### Post by lawngn0mex on 2006-07-02
[QUOTE=tommohawk][http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)[/QUOTE]


Worked for me on an install that's FAR from clean. :) thanks! :D

---

### Post by suloku on 2006-07-03
I love you man! Finally I reactivated the ******* 3d! Above 1000 fps are roported by glxgears.

But there's one thing that I just have seen, when I quited tuxraceer (for testing the 3d) this is shown:

suloku@ubuntu:~$ ppracer
PPRacer 0.3.1 --  [http://racer.planetpenguin.de](http://racer.planetpenguin.de)
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

open /dev/sequencer: No such file or directory
FATAL: fglX11FreeBuffer: firegl_FreeBuffer() failed!


It doesn't sound very well...maybe i'll try that wiki.

---

### Post by ViX666 on 2006-07-05
Quick Config - Dapper amd64 on HP dv5120us with Turion 64 and Radeon 200m Xpress.

After having followed all the steps Galban (#1), I still can't get 3D acceleration to work! :( 

(Note - after the steps, glxinfo was giving "libGL.so.1 - No such file or directory". this was overcome by - sudo ldconfig)

now, glxinfo gives:
name of display: :0.0
Error: couldn't find RGB GLX visual

Is there still no way of getting 3D acceleration to work on AMD64? I'm on the verge in trashing this install in favor of the 32bit one.. Any suggestions?

---

### Post by d-E-a-D on 2006-07-05
Ok, after more than 10 formats and thousand tries to make it work, i get 8.26 drivers working on my hp pavilion dv5172 with ati radeon Xpress 200m.
***_I'm using UMA+SIDEPORT 128Mb._***
It gives me the right fglrxinfo:

OpenGL vendor string: ATI technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5879 (***_8.26.18_***)

Now my issue is that glxgears and fglx_gears hangs when i try to run it _***but things like screensaver and games do it great on OpenGL and fps.***_ but it is unstable. sometimes crash, others not.

The worst issue is that it seems that it doesn't refresh the image, everything just is it seems that the windows are over ones of the others, I see the images overlapped, icones disappears when I open something over them and closes.
To read console i have to underline the mouse over the letters. but if i maximize the console i can read it all great.

Now the steps.
Fresh Install of Ubuntu 6.06
update
distro-upgrade
restart
follow this thread but ***_WITH 8.26.18 DRIVER DOWNLOADED FROM ATI_***:
[http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m]("http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m")
restart

For now i can't go further... does anyone goes further than this with 8.26.18 drivers?

NOTE: 8.24.18 drivers worked for me with the thread i said. but i can't get XGL and COMPIZ working. And with fglx_glxgears i just see one piece rolling, the others don't appear like in glxgears.

If someone have this 200M card working well and with XGL and COMPIZ please give us a HOW-TO step by step !!!!

SORRY MY BAD ENGLISH.

Cumps

---

### Post by tommohawk on 2006-07-06
[QUOTE=d-E-a-D]

If someone have this 200M card working well and with XGL and COMPIZ please give us a HOW-TO step by step !!!!

SORRY MY BAD ENGLISH.

Cumps[/QUOTE]

Please read this thread completely.  I have already posted how to get this card working.

The Ubuntu wiki clearly states that the 8.26.18 drivers are not stable with the 200M card.

Please listen to me.....  You must use the 8.24.8 drivers if you want 3D accel and Xgl.  Do not be tempted to install other versions - they are not stable.  Sometimes they will work and sometimes they will not.

Please - use the 8.24.8 drivers.  I have been using Dapper for some time now since early Beta days and I have always managed to get 3D working.

I have a stable HP dv8000 laptop with Xpress200M card running Dapper with Gnome running on an Xgl desktop.  Everything works and it doesn't crash or freeze.

Follow the instructions earlier in this post (page 3 I think) and if you have any questions please post back.

---

### Post by ViX666 on 2006-07-07
> **tommohawk said:**
> Please read this thread completely.  I have already posted how to get this card working.

The Ubuntu wiki clearly states that the 8.26.18 drivers are not stable with the 200M card.

Please listen to me.....  You must use the 8.24.8 drivers if you want 3D accel and Xgl.  Do not be tempted to install other versions - they are not stable.  Sometimes they will work and sometimes they will not.

Please - use the 8.24.8 drivers.  I have been using Dapper for some time now since early Beta days and I have always managed to get 3D working.

I have a stable HP dv8000 laptop with Xpress200M card running Dapper with Gnome running on an Xgl desktop.  Everything works and it doesn't crash or freeze.

Follow the instructions earlier in this post (page 3 I think) and if you have any questions please post back.


**aarrgh** now you tell me! ](*,) 
actually, it was my bad that i d/l and installed the 8.26.18 drivers (first the 64 bit and then the 32 bit over a FRESH install). when everything went to hell and beyond, i read the wiki [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#HP_Notebook_dv5029us_.2F_dv5040us_.2F_zv6000]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#HP_Notebook_dv5029us_.2F_dv5040us_.2F_zv6000")
and found: 
> * Ubuntu FGLRX drivers 8.25.18, do not work properly on the dv5029us (Radeon Xpress 200M) as of this writing (5/30/2006). It is needed to revert to 8.24.8 for this specific computer in order to get proper 3D acceleration, and 2D with no tearing off.

** ATI Driver 8.26.18, does not work with the Radeon Express 200M. Some HP/Compaq laptops only have working 3D support with ONLY UMA video memory( Sideport+UMA won't work ). This is due to a 1 year old flaw in the ATI driver. If you want to use your onboard/Sideport memory, you can only get 2D support by adding [ Option "no_dri" "yes"] to the fglrx driver section of /etc/X11/xorg.conf


d'oh! now i'll try installing 8.24.8 over the existing install and if it doesn't work, i'll try it with a fresh install..

---

### Post by d-E-a-D on 2006-07-07
> **tommohawk said:**
> Please read this thread completely.  I have already posted how to get this card working.

The Ubuntu wiki clearly states that the 8.26.18 drivers are not stable with the 200M card.

Please listen to me.....  You must use the 8.24.8 drivers if you want 3D accel and Xgl.  Do not be tempted to install other versions - they are not stable.  Sometimes they will work and sometimes they will not.

Please - use the 8.24.8 drivers.  I have been using Dapper for some time now since early Beta days and I have always managed to get 3D working.

I have a stable HP dv8000 laptop with Xpress200M card running Dapper with Gnome running on an Xgl desktop.  Everything works and it doesn't crash or freeze.

Follow the instructions earlier in this post (page 3 I think) and if you have any questions please post back.

yes, i know, as i said it works with 8.24.18... and now i've returned to 8.24 again. now my issue is to put XGL and Compiz working... 
Can you tell us step-bye-step and with the issues you found with our card, how do you do it?
Thanks!!

---

### Post by tommohawk on 2006-07-07
> **d-E-a-D said:**
>  now my issue is to put XGL and Compiz working... 
Can you tell us step-bye-step and with the issues you found with our card, how do you do it?
Thanks!!

Okay, the easiest way to get Xgl and Compiz working is to use the instructions in this link [http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389")

It is fairly easy to set up with this guide and you should get it working straight away.

Any problems - post back.

---

### Post by d-E-a-D on 2006-07-07
hmmm do you followed normal how to or session how to?

---

### Post by tommohawk on 2006-07-07
> **d-E-a-D said:**
> hmmm do you followed normal how to or session how to?

You need to follow the Session how to - method 2 - thats what worked for me.  You do need to play a little once you have installed it - mine worked almost perfectly the first time - took about 5 minutes - just make sure you install gset-compiz via synaptic aswell - this lets you configure compiz via a gnome GUI.

---

### Post by d-E-a-D on 2006-07-07
> **tommohawk said:**
> You need to follow the Session how to - method 2 - thats what worked for me.  You do need to play a little once you have installed it - mine worked almost perfectly the first time - took about 5 minutes - just make sure you install gset-compiz via synaptic aswell - this lets you configure compiz via a gnome GUI.

Thank you!!! it's working!! very easy!! thank you!!!...
Now... it's very unstable... it keeps crashing and i have to button shutdown.
Opening terminal or browser... it crash.
i can open gset-compiz... i've tried to turn off all plug-ins but it does crash anyway...

Can someone help me?

Cumps

---

### Post by ViX666 on 2006-07-07
ITS ALIVE! finally got the bloddy ati(8.24.18) drivers to work with Radeon 200M xpress!!

Here is the list of steps is followed (thanks to tomohawk and galaban)
-----------------------------------------------------------------------
Steps:

1. Clean Dapper Install.

2. Upgrade and update everything.
3. Download the 8.24.8 drivers from the ATI website.
4. Build the ubuntu packages from these drivers.
5. Recompile the Kernel.
6. Extract the libGL.so.1.2 driver from the ATI package you downloaded in step 3.
7. Replace the libGL.so.1.2 file in /usr/lib
8. Remove and *mesa* files from /xorg/fglrx and place the libGL.so.1.2 file in that directory also.
9. Configure your xorg.conf file in accordance with previous posts in this thread.
10. Blacklist the fglrx driver as detailed above.
11. Reboot and all should work.

Steps 1-5 ([http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually) )
Method 2: Generating/Installing Ubuntu packages for the 8.26.18 drivers in Ubuntu Dapper Manually

Important Change: Installation of this driver no longer requires removing the linux-restricted-modules package in order to work. There is a new blacklist feature in Ubuntu Dapper that you can use to go around this.
Installing the new driver

Download the ATI driver installer: 32bit Installer

This guide refers to the 32bit version of the driver. If you are using a x86_64 System you need the 64bit Installer. The installation procedure should be the same as for 32bit, except some filenames will differ slightly.

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

Install necessary tools:

sudo apt-get update

sudo apt-get install module-assistant build-essential 

sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

Create .deb packages:

chmod +x ati-driver-installer-8.26.18-x86.run

./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper

Install .deb packages:

sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb

sudo dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb

sudo dpkg -i fglrx-control_8.26.18-1_i386.deb

Remove any old fglrx deb's from /usr/src/:

sudo rm /usr/src/fglrx-kernel*.deb

Compile the kernel module:

sudo module-assistant prepare

sudo module-assistant update

sudo module-assistant build fglrx

sudo module-assistant install fglrx

sudo depmod -a

Note: You have to recompile the kernel module after each kernel update!

Update the xorg.conf file:

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

Reboot.

Steps 6-8 ([http://www.ubuntuforums.org/showthread.php?t=197471](http://www.ubuntuforums.org/showthread.php?t=197471))

From nautilus find inside of it ( /yourHome/someWhere/extracted )this file --> libGL.1.2.so and copy/paste it some where you can easily navigate to from your terminal.
14.-Now copy it where it will be founded by fglrx module (in my case was at /usr/lib/. From a terminal type this: sudo cp /yourHome/someWhere/extracted/libGL.so.1.2 /usr/lib/

Clean up /usr/lib/ of libGL.so.1.xlibmesa and put atiogl_a_dri.so at right place! I explain....
Put some where else your libGL.so.1.OLD or any other libGL.x.x.so version than that one extracted from the Old Ati's installer, NOT at /usr/lib/. Lets say you can move it to your /home/. Make a copy paste of your libGL.so.1.2 to your /usr/lib/fglrx/ directory too. See if there any remaining libGL.so.1.xlibmesa or any other "libGL.so" than that one extracted from the Old Ati's Installer version, if yes move it to your home, but mainly don't leave it anywhere in your /usr/lib/.../.../ !!
One last thing that I have said here is that I did and maybe it makes it works for me was that I created a directory named "/dri/ " in /usr/lib/ and after a search looking for this file --> atiogl_a_dri.so, after find it, I copy/paste it to /usr/lib/dri/ wich give you this ---> /usr/lib/dri/atiogl_a_dri.so.

IMPORTATNT NOTE: if there is the Mesa's version of libGL.so at /usr/lib/, you are gonna get Mesa appearing after fglrxinfo, if there is none, you are gonna get none from fglrxinfo, if there are both it gonna pick the Mesa's one any ways, but if there is one extracted from an old Ati's driver installer version ( 8.24.8 and before) you should get your fglrx-driver to work following the how to. That's all what I did to succesfully get back 3D acceleration. A fresh install and each and one by one of the steps on this HowTo. The proof of what I'm saying about "libGL.x.x.so" is this thread opened by myself couple weeks ago. --> [http://www.ubuntuforums.org/showthread.php?t=184627](http://www.ubuntuforums.org/showthread.php?t=184627)

Step 9

([http://www.ubuntuforums.org/showthread.php?t=197471](http://www.ubuntuforums.org/showthread.php?t=197471) )

sudo gedit /etc/X11/xorg.conf

add this (in red) to your graphic card section and SAVE it:

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
Driver "fglrx"
BusID "PCI:1:0:0"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "UseInternalAGPGART" "no"
EndSection

Add this lines to your /etc/modules and SAVE it:
agpgart
fglrx
dri

Make links to your dri modules:

Code:

sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri


Step 10

([http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually) )
blacklist old fglrx module from linux-restricted-modules

sudo gedit /etc/default/linux-restricted-modules-common

Edit DISABLED_MODULES to include fglrx

File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"

---

### Post by tommohawk on 2006-07-07
> **d-E-a-D said:**
> Thank you!!! it's working!! very easy!! thank you!!!...
Now... it's very unstable... it keeps crashing and i have to button shutdown.
Opening terminal or browser... it crash.
i can open gset-compiz... i've tried to turn off all plug-ins but it does crash anyway...

Can someone help me?

Cumps

Can you post your xorg.conf file please and the output of fglrxinfo and glxinfo.

Thanks,

---

### Post by d-E-a-D on 2006-07-07
ok... so...
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader,
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3,
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```

```
 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)

```

```
xorg.conf
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
	Option		"XkbLayout"	"pt"
	Option		"XkbVariant"	"pt"
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
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
#VideoRam	128000
#Option		"UseFBDev"		"true"
#Option "no_dri" "true"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "UseInternalAGPGART" "no"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800"
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

if I comment: 
```
#Option "VideoOverlay" "on"
#Option "OpenGLOverlay" "off"
#Option "UseInternalAGPGART" "no"
```
nothing changes...


PROBLEM SOLVED!!! I HAVE MY XGL FULLY WORKING!!!

Just add this 2 your xorg.conf:
```
Option       "KernelModuleParm" "agplock=0"
```


Cumps

---

### Post by Simpele on 2006-07-08
> **rekahsoft said:**
> Ok...i have done everything now and am getting the following error when i try fglrxinfo:
```
collin@RekahSoft:~$ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```


I've got exactly the same thing. I tried a lot of symbolic links, but nothing seems to work. I've got Kubuntu Dapper 64-bit with ATI Radeon 9200.

---

### Post by tommohawk on 2006-07-09
> **d-E-a-D said:**
> 

PROBLEM SOLVED!!! I HAVE MY XGL FULLY WORKING!!!

Just add this 2 your xorg.conf:
```
Option       "KernelModuleParm" "agplock=0"
```


Cumps

Sorry I didn't post back straight away - been a it busy with other stuff.

Exactly right - that's what I was going to suggest you do.

When you are running Xgl do you still hae the shutdown button available or only logout?

---

### Post by freelock on 2006-07-10
Hi,

Finally got accelerated graphics with fglrx on my Radeon Mobility 9000 with this tutorial. Thanks!

But it's now broken again... twice.

I installed 8.26.18 from the ATI web site, applied all the steps in the howto and got it running. But it doesn't seem that stable. It froze on me once, while changing some of the compiz settings, and then it wouldn't start compiz anymore after a hard reset. Compiz just exited with no message. fglrxinfo and others gave an XLib warning that the XFree86-dri module was missing, and modprobe dri gave a module not found error.

I tried using dpkg-reconfigure on compiz, compiz-gnome, and xserver-xgl, and something reset itself--on a subsequent reboot, everything worked again. It ran overnight with no problems. I tried logging out and going to a non-XGL session so I could suspend the laptop, and it didn't work--it appeared to suspend but the fan was still running, and the laptop beeped when I disconnected the power. So I shutdown.

After booting the laptop, I'm getting the same XLib error if I start XGL, and am not getting compiz to work. Same effects as before--under XGL, I get an Xlib warning about DRI, and I can't modprobe the dri module at all. Under normal X, everything seems normal--glxinfo reports Direct Rendering On, I get decent fps, etc. The dpkg-reconfigure steps I took earlier didn't do anything to fix the problem, either.

Any ideas on fixing this? Where does the dri kernel module get put, and why  would it disappear? Should I just downgrade to the 8.24.* driver?

Thanks,
John

---

### Post by devnulljp on 2006-07-10
> **danoyoto said:**
> noob question,

how do I go about finding out what my kernel version, restricted-modules, etc. are?

uname -r

you can just install like this:

sudo apt-get install linux-headers-`uname -r`

(those are backticks)

---

### Post by s3ppel on 2006-07-11
Thanks mate, you just made my day!

The How-To as described on page 1 worked flawless for me - even with the newer 8.26.18 from Seveas Packages.

Big thx!

---

### Post by DarkWizzard on 2006-07-13
Thank you very much.It worked. ;)

---

### Post by Malac on 2006-07-18
Indeed it worked for me too and I had just about given up.
Having tried all the dirvers and walkthroughs I could find to no avail I came across this one and it worked perfectly for me.
Heres my output from $ glxgears -printfps
```
3701 frames in 5.0 seconds = 740.009 FPS
3700 frames in 5.0 seconds = 739.807 FPS
3699 frames in 5.0 seconds = 739.610 FPS
3696 frames in 5.0 seconds = 739.112 FPS
3699 frames in 5.0 seconds = 739.746 FPS
3699 frames in 5.0 seconds = 739.708 FPS
3699 frames in 5.0 seconds = 739.681 FPS
3700 frames in 5.0 seconds = 739.831 FPS
3698 frames in 5.0 seconds = 739.449 FPS
3695 frames in 5.0 seconds = 738.997 FPS
```
Thanks Loads.

---

### Post by dmo580 on 2006-07-18
I'm running a Dell 600m laptop with ATI Mobility Radeon 9000. I followed all the steps word for word by the OP and I even looked at some other posts in this thread including:

[http://www.ubuntuforums.org/showpost.php?p=1164904&postcount=28](http://www.ubuntuforums.org/showpost.php?p=1164904&postcount=28)

I checked with that every step of the way and I have ZERO mesa files in my /usr/lib or in my /usr/lib/fglrx/

Yet when I do a fglrxinfo I still get Mesa =/ Yes I have rebooted and this is a fresh installation of Dapper.

Sorry I'm a linux newb =(

---

### Post by Mats962004 on 2006-07-20
I have insalled the ati drivers but i am not able to get into x after switching to fglrx.This is the error i am getting
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers/fglrx_drv.so [0xb73c1530]
3: /usr/bin/X(LoadModule+0xa79) [0x80a2b56]
4: /usr/bin/X(xf86LoadModules+0x96) [0x809d990]
5: /usr/bin/X(InitOutput+0x2e2) [0x809dcc3]
6: /usr/bin/X(main+0x292) [0x806debe]
7: /lib/tls/libc.so.6(__libc_start_main+0xd4) [0xb7dcdea4]
8: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 4.  Server aborting
Has anyone seen this before.I've installed the ati drivers before and never had a problem.It starts with the radeon driver no problem.Its a 9200 radeon   with 256mb ram.Any help or would be appreciated.

---

### Post by kochab on 2006-08-05
Hi,
this worked also for me (radeon 9100 R200 QM),
did anyone try the new 8.27 ati drivers?
do they work with R200 cards without changing the ligGL file?
thanks

---

### Post by bobbyw on 2006-08-14
after doing all this I get this:
meathead@quack:/usr/lib/fglrx$ fglrxinfo
fglrxinfo: error while loading shared libraries: /usr/lib/libGL.so.1: invalid ELF header
anyone know how to fix this problem?

---

### Post by rekahsoft on 2006-08-14
Could someone post an updated how-to for getting fglrx (8.27.10) working with Radeon 200M Graphics cards...I have yet to get it working. Thanx

---

### Post by Malac on 2006-08-20
Okay, just a heads up as the new 8.28.8 installer from ATI website worked perfectly for my system.
I now have fglrx working this is what I did.
[COLOR=Blue](The [COLOR=Black]**rm**[/COLOR] and [COLOR=Black]**rmdir**[/COLOR] commands are only needed if you have other driver debs in the directory from previous installs and can be missed out if you wish to keep them.)[/COLOR]
Put installer in /usr/src/ then ran following commands
In a **_root_** terminal 
[LEFT]```
cd /usr/src/
```    
[/LEFT]
 [LEFT]```
rm /usr/src/modules/fglrx/debian/*.*
rm /usr/src/modules/fglrx/*.*
rm /usr/src/ATI/*.*
rmdir /usr/src/modules/fglrx/debian
rmdir /usr/src/modules/fglrx
rmdir /usr/src/ATI
rm fglrx.tar.bz2
rm fglrx-*.deb
rm xorg-driver-fglrx*.deb
./ati-driver-installer-8.28.8.run --buildpkg Ubuntu/dapper
dpkg -i *.deb
module-assistant prepare,update
module-assistant build,install fglrx
depmod
```[/LEFT]
  
 Reboot and voila.
If you don't run this in a root terminal you will need **sudo** before each command

fglrxinfo output :
[LEFT]```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8 )
```[/LEFT]
  glxgears output :
[LEFT]```
4078 frames in 5.0 seconds = 815.554 FPS
4077 frames in 5.0 seconds = 815.391 FPS
4077 frames in 5.0 seconds = 815.330 FPS
4077 frames in 5.0 seconds = 815.383 FPS
4078 frames in 5.0 seconds = 815.418 FPS
4077 frames in 5.0 seconds = 815.371 FPS
```[/LEFT]
  Hurrah!

---

### Post by rekahsoft on 2006-08-21
ok...good news and bad news...lets start off with the good...i succesfully installed fglrx...ok...now the bad...The first time i rebooted all the graphics where wierd...so i rebooted again and X didn't load...(just a blank screen)...i am pretty sure this can be fixed by modifying /etc/X11/xorg.conf just i don't know what to add...can someone who has the Radeon 200M working let me know what to add (or post thier xorg.conf file)...Note that i am using fglrx 8.28.8. Thanks

Edit: Here is my xorg.conf:```

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
	InputDevice    "Synaptics Touchpad"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	VideoRam    256000
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
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
```

---

### Post by K.Mandla on 2006-08-22
I think I had the same problem as you with a 200m on an HP zv6000. I installed the 8.28.8 drivers and got a sloppy desktop environment that left scraps of windows everywhere. Later reboots gave me a dead black screen. I'm still hunting down the magic bullet for this one.

---

### Post by rekahsoft on 2006-08-22
hmm...ok...have you tried any older drivers? I have a compaq R4000 series laptop.

---

### Post by K.Mandla on 2006-08-22
I tried 8.27.something, with the same effect. I also tried a Xubuntu installation, just for kicks.

Invariably I get a splotchy desktop with pieces missing. Most buttons and drop-down menus don't appear unless I roll over them. It's a mess, I tell ya. 

Is there a different version of the driver I might try? Even the newest don't seem to do the trick.

---

### Post by K.Mandla on 2006-08-22
Here's a screenshot of the sloppy desktop. It might help, if you know how to fix this.

If I switch back to "ati" in my xorg.conf, it works fine. But no love from the fglrx methods.

:(

---

### Post by rekahsoft on 2006-08-22
yeah...i get the same issue...everything is tottaly messed...mine is even worse...it sucks...it is not usable...i'm thinking we can maybe add something to our xorg.conf to fix it but it may be the drivers...we should file a bug at ati's site...but i hope it doesn't come to that...i want to get it working...btw...people from this forum report getting the 8.24.8 drivers working with the Radeon 200M...maybe it is just laptop specific (hp/compaq laptops...but there is people reporting that they have it working...)

---

### Post by stereosanctity on 2006-09-26
hi i've got an hp dv5000 series notebook  running on dapper amd64 kernel with this evil ati radeon xpress 200M card.I've fisrt tried the wiki but got a buffer (RGBA i think) error!So i tried my luck following vix666's instructions two pages before which are the wiki ones plus 4-5 more.No i got this  


fgl_glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

any help plz?

---

### Post by bonewhat on 2006-09-27
Thank you :-D

However the following link was the thing that cleared the situation:
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/49900](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/49900)

I dont know if it has been mentioned anywhere but I had to rename libGL.so.1.2 to libGL.so.1 in /usr/lib



Inspiron 8200:

```
steinar@bonelap:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)

steinar@bonelap:~$ glxgears -printfps

10162 frames in 5.0 seconds = 2032.250 FPS
10125 frames in 5.0 seconds = 2024.841 FPS
9947 frames in 5.0 seconds = 1989.257 FPS
9761 frames in 5.0 seconds = 1962.087 FPS
```

(insane fps, but its running in a small window)

---

### Post by xtaz on 2006-10-14
Hi !

I did exactly all what you said on this post but when I start ubuntu I have a black screen and not the login/password screen ! (My configuration is HPdv5000 with Xpress 200M Radeon ATI)

So  I started in Rescue mode and when I tape fglrxinfo I have this message "
Error Unable to open diplsay : 0"
AS you said I copied the libGL* to my /home directory

Can you says me please what type of command I can use to detect the origin of the problem.

Thanks all ;)

---

### Post by eksir on 2006-10-17
hello.  i have a compaq lappie w/ ati mobile radeon xpress 200m 5955.

i am using the ati driver version:
8.29.6 

with Xubuntu.

i followed this tutorial:

[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)


and got nice results.  as a matter of fact,  i can now play cs 1.6 in opengl (plus glmatrix screensaver works better than ever)

i figured id post this in case it hel!ps somebody.

gl,  and hf

---

### Post by treaderll on 2007-02-12
It works!!!  I have tried many unsuccessful methods since I got this computer in April.  It has a Radeon Xpress 200 embedded on an Intel D101GGC motherboard.  I was ready to settle for 600x800 Edgy gave me, when your method came along.  I am one happy camper.

  Now to get a Cirrus driver working on that dinosaur cdrom server I got cheap.

Thank you
Treaderll

---


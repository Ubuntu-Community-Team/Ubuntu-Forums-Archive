---
title: "[SOLVED] 3D acceleration works or not"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by matjaz on 2007-12-29
Hi 
I have a problem with my 3D acceleration.
The main problem is that it sometimes works, and sometimes it doesnt.
For instance if i my 3D works and i restart my cpu, it might not work on reboot ( i DO NOT update my system in the mean time and I have to confirm an update when i want it to be installed ) , and vice versa.
I have Ubuntu 6.06 release, ATI Radeon 9600 video card, AMD Semepron 3000+ 64bit cpu,
and am running i386 instalation of Ubuntu.

I would like to know which part of my cpu "decides" whether the 3D will work or not, and why this happens ( why does my computer have mood swings ? ) ?

I am am attaching my Xorg.0.log (s) and my xorg.conf file. 
Those with GW suffix were used whet Graphics Worked, and the others when it didn't.
The xorg.conf was the same on both occasions.

I know that my xorg.conf is a mess, mostly because i tried to get the 3D working a coupple of times before i got it done. 
When i did that i mostly followed
[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
and the last time when i was 

I tried to figure out what is the diference between the two Xorg.0.logs (with diff utility) and the first diference was the line 195 in Xorg.0.log_GW.
It seems that module i2c is not loaded when 3D doesn't work.
I don't know why this happens and i have no idea how to fix it.

Shold i include some more information on my system or how i got my xorg.conf in the state it is in now?

Any suggestions would be apreciated
Matjaz

---

### Post by matjaz on 2007-12-29
Some more info on my system:
I am running dual boot system with WinXP sp2.

And another thing:
when the 3D acceleration does not work the module i2c does not seem to be loaded.
( when accel. worked i didn't check lsmod | grep i2c to see if it is loaded. I will do that next time it works, but i don't know when that will happen )
So i tried to load it manually ( when accel. did not work ): (my terminal session)
```

matjaz@matjaz-desktop:~$ glxinfo | grep rendering
direct rendering: No
matjaz@matjaz-desktop:~$matjaz@matjaz-desktop:~$ sudo su
Password:
root@matjaz-desktop:/home/matjaz# lsmod | grep i2c
i2c_acpi_ec             5120  1 acpi_sbs
i2c_nforce2             6912  0
i2c_core               21904  2 i2c_acpi_ec,i2c_nforce2
root@matjaz-desktop:/home/matjaz# modprobe /usr/lib/xorg/modules/libi2c.so
FATAL: Module /usr/lib/xorg/modules/libi2c.so not found.
root@matjaz-desktop:/home/matjaz# cd /usr/lib/xorg/modules
root@matjaz-desktop:/usr/lib/xorg/modules# ls
drivers      libcfb32.so  liblayer.so     libshadow.so     libxf8_32bpp.so
extensions   libcfb.so    libmfb.so       libvbe.so        libxf8_32wid.so
fonts        libddc.so    libpcidata.so   libvgahw.so      linux
input        libexa.so    librac.so       libxaa.so        multimedia
libafb.so    libfb.so     libramdac.so    libxf1bpp.so
libcfb16.so  libi2c.so    libscanpci.so   libxf4bpp.so
libcfb24.so  libint10.so  libshadowfb.so  libxf8_16bpp.so
root@matjaz-desktop:/usr/lib/xorg/modules# modprobe libi2c.so
FATAL: Module libi2c.so not found.
root@matjaz-desktop:/usr/lib/xorg/modules# modprobe libi2c
FATAL: Module libi2c not found.
root@matjaz-desktop:/usr/lib/xorg/modules#

```

so it seems i can't load that module, even though it is there: it si invisible to the modprobe.
Or I am misusing modprobe, and in that case I would apreciate if you tell me how to load a module manually.

---

### Post by matjaz on 2007-12-30
I have just discovered that 3D acceleration seems to work whenever i boot linux directly after a boot of windows- if i boot Win and then restart to linux, 3D works, and even if i restart my cpu and boot linux again it still works.
But if i turn it off and then boot linux, acceleration doesn't work anymore.
This is my booting sequence:

cpu turned off: boot Win
restart to Lin - 3D works
restart to Lin - 3D works
i turn off the cpu
i boot Lin - 3D does not work
restart to Lin - 3D does not work
restart to Win
restart to Lin - 3D works

and when i booted to Lin i just tried to play penguin racer to see if 3D works or not and mybie used lsmod and glxinfo.

And my terminal output:
```
matjaz@matjaz-desktop:~$ lsmod | grep i2c
i2c_acpi_ec             5120  1 acpi_sbs
i2c_nforce2             6912  0
i2c_core               21904  2 i2c_acpi_ec,i2c_nforce2
matjaz@matjaz-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
matjaz@matjaz-desktop:~$ glxinfo
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
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)
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
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
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
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
matjaz@matjaz-desktop:~$

```

So what can I do to make the 3D acceleration work every time i boot Linux?

---

### Post by mgmiller on 2007-12-30
This is just a guess, but it sounds like windows is enabling something by software, that should be set in the BIOS.

Try going into your BIOS and go to the agp section and see if agp fast writes is enabled.  If it is, try disabling it, if it isn't, try enabling it.  Also, while you're in BIOS, make sure the agp multiplier is set correctly for your video card.  (If it's an 8x card, make sure agp is set to 8x, etc.)

---

### Post by matjaz on 2007-12-30
First thanks for your suggestion.

I have tried to find the AGP multiplier  in BIOS, but the only things i could find that had AGP in their name were:
AGP FW Enable : (Disable / Auto)
AGP SideBand Address : (Disable / Auto)

I have tried setting them on every possible combination of disable / auto and the acceleration didn't work, when i didn't start windows before and then restarted.

So i am now wondering if i have to upgrade my system to Ubuntu 7.10 ( i really wouldn't want to do that, i have some problems with wireless card and upgrade would force me to physicly move my computer to a place where i could get internet acces through cable for the time that i would be fixing my wireless card issues )
to get the acceleration working or is there another way to get acceleration working beacouse it does work after I restart from windows, so It can work with my current drivers.

Will the upgrade solve the problem?

But as you said, it might be a bios problem, as i do have a nForce3 motherboard, which is reported not to work with some versions of bios at least.
( [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting) )
So i just might have to upgrade / downgrade my bios, which is another thing i would like to avoid ( i have neved done anything similar ).

Another thing i would like to know is how can changing BIOS make a diference, because when i restart from windows the BIOS is loaded just the same ( or am I wrong ? ) as it is when i just start my computer ( or something that windows put in the memory stays there ? ) and load ubuntu directly, ( and on one occasion the acceleration works and on the other it doesn't ) so ( is my conclusion correct? ) the acceleration can work under my current BIOS.

So my next question is how can booting windows first make a diference that even my Ubuntu, that is booted after i restart my cpu from windows,can detect?

---

### Post by mgmiller on 2007-12-31
The FW setting is fast writes and you tried that off and on with no effect.

> Will the upgrade solve the problem?

Maybe (not a very helpful answer)


> I do have a nForce3 motherboard,

Take a look in BIOS again and see if there are areas about reposting the video BIOS on reboot.  It may not be in the same spot as the AGP stuff.

> So i just might have to upgrade / downgrade my bios, which is another thing i would like to avoid ( i have neved done anything similar ).

This is usually not too hard to do, consult the mobo makers website for details.  It usually involves creating a bootable floppy disk with the new BIOS on it as well as a small utiltiy from the mobo maker.  On booting the floppy, you just follow the prompts and point it at the new BIOS file when asked.

That being said, do this as a last resort, unless the mobo makers web forum specifically says there is a glitch that gives the exact symptoms you are having and the updated BIOS will fix it.


> Another thing i would like to know is how can changing BIOS make a diference, because when i restart from windows the BIOS is loaded just the same ( or am I wrong ? )

You are right in thinking you are wrong...LOL....
There is a difference between warm booting (restart from running OS) and cold booting (hitting the reset button or power off and then on).  
I have even seen differences between reset button and power off and on restarts.

What happens is in a warm restart, not everything in the mobo gets its memory flushed and restarted.  Settings that were made from the OS _MAY_ still remain in effect.  Note that many onboard devices like the sound system and the video card may have their own memory (especially video cards) and BIOS (this is often referred to as firmware), separate and distinct from the system memory and BIOS.  To a certain extent, you can think of each of these items as its own little computer.

So, on a warm reboot, as in restarting from Windows, your video card is not totally rebooting itself and something that the windows driver set in cards memory is not getting flushed, so when you start it in Linux, it works.

On a cold start, where the machine was off, the video card restarted from scratch and something is not getting loaded in the Linux video driver.

I hope that isn't too confusing.

Can you post the output of your xorg.conf file? Maybe I can spot something missing that needs to be there.

In a terminal type:
```
cat /etc/X11/xorg.conf
```

Then copy and paste it into your response.

Sometimes ATI video cards can be a problem to get working correctly.

---

### Post by mgmiller on 2007-12-31
You also didn't mention which mobo you have or which BIOS revision it has.
As I mentioned in my previous post it appears Asus has a BIOS revision that seems to address your problem, but I don't know if you have an Asus mobo.

I just followed the link you gave in your last post and it lists a series of very good steps to try to get the video working.  Did you try them?
For example, what is the output of:
```
fglrxinfo
```

Try this both after a warm boot when 3D works and then a cold boot where it does not.

---

### Post by mgmiller on 2007-12-31
I just noticed you posted your xorg.conf in your first post.

I think I see a problem in it.  You are loading your video card driver twice and using 2 different drivers:

```
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```


In the first, you are loading the ati driver and then in the second, you are loading the fglrx driver.


Here is what I would try.

First make a backup copy of your xorg.conf
```
sudo cp /etc/X11/xorg.conf xorg.conf.backup
```

Then, edit your xorg.conf as follows:
open the file for editing:
```
gksudo gedit /etc/X11/xorg.conf
```

Then scroll to the device section where the 2 entries shown above are listed.

You want to replace the 2 device entries with only the following:
```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
        Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```


Save the file and try a power off and on reboot.
If it gives you problems, edit the file and put a comment in front of the BusID and option lines like this:

```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	# BusID       "PCI:1:0:0"
        # Option	    "VideoOverlay" "on"
	# Option	    "OpenGLOverlay" "off"
EndSection
```

Then save and restart and try removing one of the comment tags (#) at a time to see which is causing the problem.

In case you have no x and are stuck in command line, from the command line you would enter the command:
```
sudo nano /etc/X11/xorg.conf
```

This will open the file for editing in a "DOS-like" editor.

Use your arrow keys to scroll down to the area you want to edit and make the changes, then to save the file hold the ctrl key and hit the letter o 
it should show the name of the file to write near the bottom of the screen, just hit enter to save the file.

To exit the editor, hold ctrl and hit x

Try to restart x
```
startx
```

or just restart the computer.

If all else fails and you are stuck in the command line and can't get x running, restore your backup.  From the command prompt type:
```
sudo cp /etc/X11/xorg.conf.backup xorg.conf
```

Good luck.
I think the primer is dry and I need to go back to painting my kitchen now.

---

### Post by matjaz on 2008-01-03
I have found my motherboard manual :( and it says that it is a :
-Asus K8N motherboard
-Socket 754 for AMD CPU
-NVIDIA nForce3 250
-.... (some other data)

And at the same time in [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting) :
K8N Bios versions up 1003 to 1011, my Solution -> K8V-X (Asus with Via-Chipset) It is working really good now. (Always Problems: nForce3 Chipset)

So it seems that it shouldn't have worked anyway...
Does the line abowe mean that i can get it to work by getting the BIOS for K8V-X or I have to get that chipset ( probably the chipset ).

But i tried what you suggested anyway.
After i deleted that "ATI Technologies ..." Device, i got an error: Undefined reference "ATI ... " in Default Screen. I fixed that too, eventually.
I am including my mew xorg.conf .
And i tried my fglrxinfo output in both cases.
I did try all those methods in the wiki and manny others.
To give you an idea how i got my xorg.conf in such a messy state i am including a list of all the backups i made.. one attempt for every backup:)

so here is my terminal output:
```
booted directly to ubuntu:
matjaz@matjaz-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
matjaz@matjaz-desktop:~$

warm boot:
matjaz@matjaz-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)

matjaz@matjaz-desktop:~$

all xorg.conf:
matjaz@matjaz-desktop:~$ cd /etc/X11
matjaz@matjaz-desktop:/etc/X11$ ls | grep xorg.conf
xorg.conf
xorg.conf~
xorg.conf.20071225112928
xorg.conf.20071225123358
xorg.conf.20071225124539
xorg.conf.20071225124649
xorg.conf.20071225145121
xorg.conf_25_12_2003_4-ta_dela_z_grafiko
xorg.conf_25_12_2007
xorg.conf_25_12_2007-2
xorg.conf_25_12_2007_3
xorg.conf_back_26_12_2007-1
xorg.conf_back3
xorg.conf_backup4
xorg.conf.fglrx-0
xorg.conf.fglrx-1
xorg.conf.fglrx-2
xorg.conf.fglrx-3
xorg.conf.fglrx-4
xorg.conf.fglrx-5
xorg.conf.fglrx-6
xorg.conf_ko_grafika_dela
xorg.conf.original-0
xorg.conf.original-1
xorg.conf.original-2
xorg.conf.original-3
xorg.conf_pospesevanje-ne_resolucija-ok
matjaz@matjaz-desktop:/etc/X11$

new xorg.conf:
matjaz@matjaz-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

matjaz@matjaz-desktop:~$

```

Thanks for all the help.
I only have the question about BIOS left and it would help me if you can tell which answer is the right one, thow i don't seriously believe that changing BIOS would help.

As it seems that the acceleration should have never worked anyway, I am marking this thread as solved

Thanks again.

And happy new year:)

---

### Post by mgmiller on 2008-01-03
> I only have the question about BIOS left and it would help me if you can tell which answer is the right one, thow i don't seriously believe that changing BIOS would help.


What you found in the wiki is interesting information.

> (Update: March 22nd, 2007) It appears that the beta ASUS bios 1012 will also fix the problem. I had the ATI drivers installed but fglrxinfo was still reporting Mesa as the OpenGL provider. I flashed the BIOS to 1012, rebooted into Ubuntu. Problem solved.

> And at the same time in [http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting) :
K8N Bios versions up 1003 to 1011, my Solution -> K8V-X (Asus with Via-Chipset) It is working really good now. (Always Problems: nForce3 Chipset)

I believe these are 2 different people reporting their experiences.  The first quote above flashed his (nforce 3) k8N-E deluxe mobo with BIOS 1012 and the problem was resolved.

The second person tried the nforce chipset drivers up to 1011 and when that didn't work, he switched motherboards to a k8v-x which has a via chipset.

Under no circumstances should you attempt to flash an nforce based mobo with a  via BIOS!!!  You stand a really good chance of "bricking" the mobo.

I would say, based on the above, that if you are still having the problems with your k8n, that you should flash to the 1012 BIOS that the wiki contributor had a good response with.

---


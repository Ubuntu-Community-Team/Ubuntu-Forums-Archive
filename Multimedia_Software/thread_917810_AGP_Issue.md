---
title: "AGP Issue"
date: 2008-09-12
forum: Multimedia Software
---

### Post by Basfriends on 2008-09-12
Hello everyone,

For a few years now I am a very satisfied Ubuntu user (started from 6.06). Since I want to grand that satisfaction to the rest of my family I attemped to install Ubuntu on the (slightly older) family desktop.

After booting I don't have hardware acceleration (or Direct Rendering). This is the case with the open source Radeon driver, as well with the closed source ATI driver. This is as far as I know due to AGP (All error messages seem to come from the driver being unable to set up AGP properly).

In the logs (which are not attached, due to size limitations) i've found the following:

messages, kern.log, syslog, dmesg:
```

agpgart: Detected AGP bridge 0
agpgart: Setting up Nforce3 AGP.
agpgart: aperture base > 4G

```

Xorg.0.log:
```

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0

[...]

//This seems ok
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0

[...]

(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.

[...]

(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled

[...]

(II) AIGLX: Screen 0 is not DRI capable


```

This is using the radeon driver. Using the fglrx driver (proprietary ATI driver) i get similar results, slightly different error messages however the "AGP Failed to initialize" error message remains present, as well as the "Aperture > 4G" message. (With composition enabled fglrx even put a white screen over my desktop, leaving only the mouse visible.)

I know there is a lot of info to be found on the net, not only on the ATI website and forums as well as here on the forums. (Yes, tried google too...) However nothing I found seems to work for me. I would not bother you before i've done several days of research.

So if there is anyone among you who recognizes this problem and could give me (some direction to) a solution that is compatible with my hardware (for intel i've found many, but i'm not using that...), i'd be forever gratefull.

Bas

---

### Post by Basfriends on 2008-09-14
Hi,

i'm still unable to solve this mistery. If there is anyone out there who can help me with this, or perhaps can give me some clues (e.g. threads i might have missed) that might work, then please do so. 

If you need more information (e.g. logs, hardware info, whatever you might need) then please let me know and i will answer as quickly and clearly as possible.

Thanks in advance,

Bas

---

### Post by skullmunky on 2008-09-16
That looks really familiar, but I can't remember exactly how I solved it.  It was a while ago....

I think it's not specifically a problem with the AGP port, exactly, but with the drivers, or to be more precise, the kernel modules.  It may be that you have kernel modules installed that are wrong for your kernel, or that there are two modules that are incompatible.  

I think what worked for me in a similar situation was some combination of blacklisting the ubuntu drivers and installing manually, and maybe waving a dead chicken a few times.

---

### Post by bandman159 on 2008-09-22
(nForce3 250, ATI Radeon 7000)
i have same issue. but Does not solve.

Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
	Option "BusType" "PCI" <-- When does is Direct Rendering activated like this.

but, i want useing AGP...

---

### Post by Basfriends on 2008-09-22
Still no luck here, i'll give the next driver released from AMD a shot. Doubt if it will make any changes, since it seems not to be a problem with the driver. I'll post my foundings soon.

Bas

---

### Post by bandman159 on 2008-09-25
i solve this problom.

open edit..

/boot/config-2.6.24-19-generic

CONFIG_AGP=m --> CONFIG_AGP=y

CONFIG_AGP_NVIDIA=m --> CONFIG_AGP_NVIDIA=y

/etc/modules Add

radeon
agpgart
nvidia-agp
intel-agp

save, and reboot

display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow

---

### Post by sultanoswing on 2008-09-25
I had a similar problem (but may not be exactly the same!!) - I solved it by going into the BIOS and setting the AGP aperture to 128MB (from default 32). Worth a shot! You might try 64, 128 and even 256MB aperture size and see what, if any, work for you.

---

### Post by tystic on 2008-10-04
The nForce3 chipset is not initializing properly with the Linux driver.

Only workaround I have found is a dual-boot setup:  boot into windows, reboot into linux, and it will read properly.  If you shut down the computer for any reason, you have to go into windows again.

I wish I could get a correct driver for this, it's the only reason I don't use Ubuntu anymore.  Every time you forget to go into windows first it makes a mess after you've set up the compiz-fusion effects.

---

### Post by linuce on 2008-11-11
From what I have googled, the problem is in the nForce3 chipset initialization. I owns a  motherboard (AM2NF3-VSTA from ASRock) with such a chipset and an AGP ATI Radeo 9250 graphic card (Sapphyre Radeon 9250) and I have the same problem: I can't get 3D desktop effects from a cold boot into Ubuntu 8.04/8.10.

The only "solution" I have found is the tystic's one: I first have to boot Windows XP before booting Ubuntu 8.04 x86 to get proper AGP initialization and 3D desktop effects.

Do NOT ever think that the problem is solved with  Ubuntu 8.10 x86: if I boot it directly from a cold boot, everything I get is a blank screen, be it from the installation CD or from an upgraded Ubuntu 8.10 x86 from Ubuntu 8.04 x86. So even with Ubuntu 8.10 x86, I have to boot Windows XP first, then Ubuntu 8.10 x86.

With Ubuntu 8.04 AMD64, same "solution": I have to boot Windows XP first then Ubuntu 8.04 AMD64 to get a proper AGP initialization. I didn't try with Ubuntu 8.10 AMD64 because I don't have any more time to try.

---

### Post by Sahtor on 2009-11-23
> **bandman159 said:**
> i solve this problom.

open edit..

/boot/config-2.6.24-19-generic

CONFIG_AGP=m --> CONFIG_AGP=y

CONFIG_AGP_NVIDIA=m --> CONFIG_AGP_NVIDIA=y

/etc/modules Add

radeon
agpgart
nvidia-agp
intel-agp

save, and reboot



Thanks this fixed my Radeon 9800 Pro XT with nForce3 chipset and Ubuntu Karmic. I had (EE) agpgart problem in /var/log/Xorg.0.log

---


---
title: "HELP!!! Problems with VIA K8M890..."
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by d_v_d on 2007-05-03
Hi!
I have a problem with installing my vga drivers. I have a K8V-VM motherboard with an integrated VIA K8M890. I've followed the instructions for installation on [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) and everything seemed to have gone well... Only I still don't have 3D...
My Ubuntu is 7.04 x86_64.
When executing
# glxgears -info
I get:

root@DVD:~# glxgears -info

GL_RENDERER = Mesa DRI UniChrome 20060710
GL_VERSION = 1.2 Mesa 6.5.2
GL_VENDOR = VIA Technology
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_APPLE_packed_pixels GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
0000: f0000001 00000300 f0000006 00000000
0010: f000000b 00000000 f000000c 0028207c
0020: f000000d 0028207c f000000e 809c009c
0030: f0000002 00000005 f0000003 00000005
0040: f0000004 012b012b f0000000 f0002001
0050: f000000b 00000000 f0000001 00000300
0060: f0000006 ffffff00 f000000b 10000000
0070: f000000c 0028d74c f000000d 0028d74c
0080: f000000e 809c009c f0000002 00000005
0090: f0000003 00000005 f0000004 012b012b
00a0: f0000000 f0002001 f000000b 00000000
00b0: f210f110 00010000 cccccccc cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
Aborted (core dumped)

I have attached my xorg.conf and modules.
Please, if someone can help me!!!

PS I think the problem may be that it doesn't recognize the VGA. When I execute:

root@DVD:~# lspci |grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 11)

But i don't know what to do...

---

### Post by Tomy on 2007-05-03
> **d_v_d said:**
> Hi!
I have a problem with installing my vga drivers. I have a K8V-VM motherboard with an integrated VIA K8M890. I've followed the instructions for installation on [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) and everything seemed to have gone well... Only I still don't have 3D...
My Ubuntu is 7.04 x86_64.
......
I don't think 3D (dri) is supported yet on the K8M890. You might ask over at openchrome.org.

Here is a recent message about the K8M890
[[html]http://wiki.openchrome.org/pipermail/openchrome-users/2007-April/003030.html[/html]]("http://wiki.openchrome.org/pipermail/openchrome-users/2007-April/003030.html")

---

### Post by Randy_84dger on 2007-05-23
Am also having trouble with VIA chipset. It seems3D acceleration is not implemented for the K8M890, see the table here:

[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats")

I guess we'll have to wait for it, don't much fancy writing it myself :D
Al.

---

### Post by xmastree on 2007-08-22
I've just installed ubuntu on an Asus K8V-VM with this graphics chip.

After reading this thread I started looking for a cheap nVidia card. :rolleyes:

Seems I can get a 256MB GeForce6200 for under £20 and I *know* it'll work just fine.

---


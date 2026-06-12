---
title: "Ubuntu 12.04.1 LTS ATI System Crash"
date: 2013-01-20
forum: Multimedia Software
---

### Post by copan on 2013-01-20
**To mods**:  This problem was reported once in General Support, but after reading the log file and pondering on the situation as to what could have been the cause, I decided the highest possibility would be a graphics issue.  However, I can't be sure and I've reposted it here.  I apologize if this is against forum rules.

Ubuntu randomly becomes unresponsive, and displays a "no" symbol, as in no smoking.  This has happened about 3 times now and seems to happen after I switch my TV input from ubuntu (HDMI 1) to XBOX 360 (ColorStream) and back again.  It does not happen every time but happens sometimes.

I have a 42" Toshiba running on Ubuntu 12.04.1 LTS 64-bit version
Processor: AMD Phenom II X6 1055T
Graphics: VESA: Redwood?  ATI Radeon card not sure what model

Anyway, my machine does not respond to anything, including:

[LIST]
[*]mouse
[*]keyboard
[*]ssh
[*]http
[*]ftp
[/LIST]

If I could even login using ssh or use the terminal I would at least try restarting lightdm or something.

Please look at my screenshot to see the symbol I get when the machine freezes.  Has anyone else had this happen to them?  Am I being hacked or something?  Seems like the machine is running but no longer accepts incoming connections or devices.

Since the keyboard was frozen the "screenshot" is actually a digital photo of the screen.

After further investigation I figured out how to locate and copy the latest from ubuntu's kernel log report - which occurred around the time of the crash.  Dump from /var/log/kern.log.1

Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.665958] [fglrx] Maximum main memory to use for locked dma buf$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666051] [fglrx]   vendor: 1002 device: 68d8 count: 1
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666438] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666450] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) ->$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666453] pci 0000:01:00.0: setting latency timer to 64
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666732] [fglrx] Kernel PAT support is enabled
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666747] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] wi$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   15.005604] logitech-djreceiver 0003:046D:C52B.0006: hiddev0,hidr$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   15.010722] input: Logitech Unifying Device. Wireless PID:1025 as$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   15.010888] logitech-djdevice 0003:046D:C52B.0007: input,hidraw4:$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   15.250858] type=1400 audit(1358674789.912:8): apparmor="STATUS" $
Jan 20 01:39:49 prissy-TA785G3 kernel: [   15.251269] type=1400 audit(1358674789.912:9): apparmor="STATUS" $
Jan 20 01:39:50 prissy-TA785G3 kernel: [   15.578359] init: failsafe main process (760) killed by TERM sign$
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917664] Bluetooth: Core ver 2.16
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917684] NET: Registered protocol family 31
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917686] Bluetooth: HCI device and connection manager initiali$
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917689] Bluetooth: HCI socket layer initialized
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917691] Bluetooth: L2CAP socket layer initialized
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917695] Bluetooth: SCO socket layer initialized
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.935434] Bluetooth: RFCOMM TTY layer initialized
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.935438] Bluetooth: RFCOMM socket layer initialized
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.935439] Bluetooth: RFCOMM ver 1.11
Jan 20 01:39:51 prissy-TA785G3 kernel: [   17.076942] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (leve$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.106776] input: HDA ATI SB Line as /devices/pci0000:00/0000:00$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.106899] input: HDA ATI SB Rear Mic as /devices/pci0000:00/000$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.106962] input: HDA ATI SB Front Mic as /devices/pci0000:00/00$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.107017] input: HDA ATI SB Front Headphone as /devices/pci0000$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.107069] input: HDA ATI SB Line Out as /devices/pci0000:00/000$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.107324] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (leve$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.107390] snd_hda_intel 0000:01:00.1: irq 43 for MSI/MSI-X
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.107408] snd_hda_intel 0000:01:00.1: setting latency timer to $
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.164970] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.164973] Bluetooth: BNEP filters: protocol multicast
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 17.333713] type=1400 audit(1358674791.996:10): apparmor="STATUS"$
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 17.334073] type=1400 audit(1358674791.996:11): apparmor="STATUS"$
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 17.346756] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci$
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 18.029552] r8169 0000:02:00.0: eth0: link down
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 18.029565] r8169 0000:02:00.0: eth0: link down
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 18.030275] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 18.030508] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.283789] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.283792] vesafb: scrolling: redraw
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.283795] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.291762] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc9$
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.291982] Console: switching to colour frame buffer device 175x$
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.292025] fb0: VESA VGA frame buffer device
Jan 20 01:39:53 prissy-TA785G3 kernel: [   19.122272] audit_printk_skb: 48 callbacks suppressed
Jan 20 01:39:53 prissy-TA785G3 kernel: [   19.122275] type=1400 audit(1358674793.784:28): apparmor="STATUS"$
Jan 20 01:39:54 prissy-TA785G3 kernel: [   20.183367] r8169 0000:02:00.0: eth0: link up
Jan 20 01:39:54 prissy-TA785G3 kernel: [   20.184160] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan 20 01:40:01 prissy-TA785G3 kernel: [   26.340660] fglrx_pci 0000:01:00.0: irq 44 for MSI/MSI-X
Jan 20 01:40:01 prissy-TA785G3 kernel: [   26.341323] [fglrx] Firegl kernel thread PID: 1265
Jan 20 01:40:01 prissy-TA785G3 kernel: [   26.341389] [fglrx] Firegl kernel thread PID: 1266
Jan 20 01:40:01 prissy-TA785G3 kernel: [   26.341454] [fglrx] Firegl kernel thread PID: 1267
Jan 20 01:40:01 prissy-TA785G3 kernel: [   26.341539] [fglrx] IRQ 44 Enabled
Jan 20 01:40:04 prissy-TA785G3 kernel: [   29.374825] [fglrx] Gart USWC size:1280 M.
Jan 20 01:40:04 prissy-TA785G3 kernel: [   29.374828] [fglrx] Gart cacheable size:508 M.
Jan 20 01:40:04 prissy-TA785G3 kernel: [   29.374831] [fglrx] Reserved FB block: Shared offset:0, size:1000$
Jan 20 01:40:04 prissy-TA785G3 kernel: [   29.374833] [fglrx] Reserved FB block: Unshared offset:f8fd000, s$
Jan 20 01:40:04 prissy-TA785G3 kernel: [   29.374835] [fglrx] Reserved FB block: Unshared offset:3fff4000, $
Jan 20 01:40:06 prissy-TA785G3 kernel: [   31.488061] eth0: no IPv6 routers present

Thank you all for your time.

---

### Post by copan on 2013-01-20
As per rrich1974

output  lspci
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Redwood [Radeon HD 5670]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```output glxinfo
```

name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_allocate_memory, GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_fbconfig_float, GLX_AMD_gpu_association
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_swap_control, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5670
OpenGL version string: 4.2.11627 Compatibility Profile Context
OpenGL shading language version string: 4.20
OpenGL extensions:
    GL_AMDX_debug_output, GL_AMDX_vertex_shader_tessellator, 
    GL_AMD_conservative_depth, GL_AMD_debug_output, 
    GL_AMD_depth_clamp_separate, GL_AMD_draw_buffers_blend, 
    GL_AMD_multi_draw_indirect, GL_AMD_name_gen_delete, 
    GL_AMD_performance_monitor, GL_AMD_pinned_memory, GL_AMD_sample_positions, 
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export, 
    GL_AMD_shader_trace, GL_AMD_texture_cube_map_array, 
    GL_AMD_texture_texture4, GL_AMD_transform_feedback3_lines_triangles, 
    GL_AMD_vertex_shader_layer, GL_AMD_vertex_shader_tessellator, 
    GL_AMD_vertex_shader_viewport_index, GL_ARB_ES2_compatibility, 
    GL_ARB_base_instance, GL_ARB_blend_func_extended, 
    GL_ARB_color_buffer_float, GL_ARB_compressed_texture_pixel_storage, 
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, 
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_framebuffer_sRGB, GL_ARB_geometry_shader4, 
    GL_ARB_get_program_binary, GL_ARB_gpu_shader5, GL_ARB_gpu_shader_fp64, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, GL_ARB_imaging, 
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_sample_shading, GL_ARB_sampler_objects, 
    GL_ARB_seamless_cube_map, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_atomic_counters, GL_ARB_shader_bit_encoding, 
    GL_ARB_shader_image_load_store, GL_ARB_shader_objects, 
    GL_ARB_shader_precision, GL_ARB_shader_stencil_export, 
    GL_ARB_shader_subroutine, GL_ARB_shader_texture_lod, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack, 
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_sync, GL_ARB_tessellation_shader, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32, 
    GL_ARB_texture_compression, GL_ARB_texture_compression_bptc, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui, 
    GL_ARB_texture_snorm, GL_ARB_texture_storage, GL_ARB_timer_query, 
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3, 
    GL_ARB_transform_feedback_instanced, GL_ARB_transpose_matrix, 
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_EXT_abgr, 
    GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_buffer, GL_EXT_copy_texture, GL_EXT_direct_state_access, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_geometry_shader4, GL_EXT_gpu_program_parameters, 
    GL_EXT_gpu_shader4, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_float, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_provoking_vertex, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, GL_EXT_texture_array, 
    GL_EXT_texture_buffer_object, GL_EXT_texture_compression_bptc, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm, 
    GL_EXT_texture_storage, GL_EXT_texture_swizzle, GL_EXT_timer_query, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_attrib_64bit, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_conditional_render, 
    GL_NV_copy_depth_to_color, GL_NV_copy_image, GL_NV_explicit_multisample, 
    GL_NV_float_buffer, GL_NV_half_float, GL_NV_primitive_restart, 
    GL_NV_texgen_reflection, GL_NV_texture_barrier, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

81 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x033 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x035 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x037 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x039 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x041 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x043 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x049 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x060 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x061 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x062 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x067 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x068 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x069 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x071 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x072 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0cb 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon

91 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x023 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x024 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x025 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x026 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x027 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x028 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x029 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x02b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x02d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x02f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x030 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x031 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x032 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x033 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x034 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x035 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x036 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x037 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x038 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x039 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x03b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x03d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x03f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x040 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x041 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x043 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x044 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x046 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x049 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x04b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x04d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x04f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x050 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x052 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x053 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x054 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x055 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x056 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x057 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x058 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  2 1 None
0x059 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  2 1 None
0x05b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x05d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x05f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x060 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  4 1 None
0x061 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x062 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 None
0x063 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x064 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x065 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x066 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x067 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x068 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  6 1 None
0x069 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  6 1 None
0x06b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 None
0x06d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 None
0x06f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x070 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  8 1 None
0x071 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x072 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  8 1 None
0x0cb 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  4 1 Ncon
0x0cb 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 Ncon
0x0cb 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x0cb 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 Ncon
0x0cb 32 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 Ncon
0x0cb  0 tc  0 128  0    y .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0cb  0 tc  0 128  0    . .  32 32 32 32 .  .  0 24  0  0  0  0  0  0 0 None
0x0cb  0 tc  0  64  0    y .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0cb  0 tc  0  64  0    . .  16 16 16 16 .  .  0 24  0  0  0  0  0  0 0 None
0x0cb  0 tc  0  32  0    y .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0cb  0 tc  0  32  0    . .  11 11 10  0 .  .  0 24  0  0  0  0  0  0 0 None

```

output fglrxinfo

```

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5670
OpenGL version string: 4.2.11627 Compatibility Profile Context

```

---

### Post by copan on 2013-01-26
*bump*

I found out that this issue has nothing to do with the "no" symbol.  I just had pressed a button on my keyboard and the feature did not exist within ubuntu, and it happened to have froze at that time.

The issue persists and I do not know why.  Can anyone be of further help, or should I file a bug?

Thank you for reading.  ):P

---

### Post by Yellow Pasque on 2013-01-26
If you suspect a graphics bug, then you may want to uninstall fglrx/Catalyst proprietary ATI driver and run the open-source driver for a while to see if the issue still occurs.

---

### Post by copan on 2013-01-27
I believe you may be correct.  I initially installed the proprietary graphics driver for ATI when I was having trouble using a high resolution when using two monitors.  However, I now just use my one big monitor and no longer require the driver.  I believe it was after this installation I first started to experience the freezing.

I will keep a look out, and if after two weeks I see no more freezing I will post this issue as solved.  It should help other people with the same issue using ATI cards.

[B]AGAIN TO SUMMARIZE FOR THOSE SKIMMING THE PAGE:

The issue was due to FGLRX proprietary driver.  The reason for installing it was better resolution on a system using TWO displays.  One being Toshiba 1080p TV and other Samsung monitor.[/B]

Thank you for your time. :KS

---

### Post by copan on 2013-01-27
I uninstalled FGLRX proprietary driver and it didn't freeze but instead the display was cut off after a period of 40 minutes inactivity.  Even though I have "turn off display" set to NEVER it still shuts off.

It won't turn the display on after clicking mouse or keyboard and reboot was required.   Next time I'll try SSH and some terminal commands.  I'll keep you posted.

---

### Post by Yellow Pasque on 2013-01-28
DPMS might be the culprit there. Check:
```
xset -q
```
and if DPMS is enabled, turn it off:
```
xset -dpms
```
^(that command may need run with sudo, but try without first)

---

### Post by copan on 2013-01-31
**EDIT: This didn't work.**

Just an update on this.. I've installed the latest Catalyst driver from ATI's web-site and if no freezing in 2 weeks I'm going to post the solution I used from Ubuntu official instruction page.

While I did use the FGLRX graphics driver, it seems to work differently and possibly better when installing using the terminal and building the package manually and following all the purge instructions for the old drivers.

If all works out I'll post the solution and update as solved.

Many thanks.

---

### Post by copan on 2013-02-01
**EDIT**

Even though I switched to Mint I still have the same issue, and like Temujin recommended, I think DPMS WAS the culprit.  I finally came up with a solution that works to turn off screensaver and DPMS.  See below:

In terminal:

1) cd /usr/bin/

2) sudo nano forcexset.sh

#!/bin/bash
xset -dpms
xset s off
xset s noblank
xset s 0 0

[SAVE FILE]

3) sudo chmod 700 /usr/bin/forcexset.sh

4) sudo /usr/bin/forcexset.sh

5) xset -q

Check  if all is disable.  It was for more.  The only problem is I can't  crontab this or use startup applications because xserver will start  AFTER and thereby override the settings the script invokes.

[COLOR=Red]***Now I will wait 5 more days and see if any freezing will persist.  If not, I will reply and tell you again to try my advice.  If freezing DOES persists, I'll just have to file a bug report and/or start a new thread.***[/COLOR]

**Be advised, you turn off DPMS with this command: xset -dpms** UNLIKE WHAT YOU SEE IN THIS POST: [http://askubuntu.com/questions/61291/how-to-permanently-disable-monitor-power-saver-using-the-command-line/251053#251053](http://askubuntu.com/questions/61291/how-to-permanently-disable-monitor-power-saver-using-the-command-line/251053#251053)

By the way, Ubuntu is still an excellent choice with the most support.  I've just been meaning to try Mint anyway.. plus it's based on Ubuntu.  So I don't want people thinking I'm bashing ubuntu.

[B]UNEDITED:
[/B]
Dear Ubuntu,

  I have been unable to fix this problem by troubleshooting.  I can no longer accept unity into my heart and have opted for Linux Mint.  :(

  It's nothing personal, I just want my server AND my media center without the freezing.

Thank you for all your help.

---

### Post by copan on 2013-02-03
*bump*

Thanks for advice on DPMS.  I just found out how to change the settings with xset and await further freezing.  Will post results in 5 days.

---

### Post by jortony on 2013-03-12
Is this actually solved, or is the switch to another distro considered a fix? I have the same symptoms, and a similar hardware build. This is the first I have read of DPMS, which in retrospect is stunning. I am so tired, I just want my computer to work.

edit. 
I have applied above script and xset -dpms, will respond in 15 minutes if I crashed in transition to standby.

---

### Post by jortony on 2013-03-12
thorough and unrelenting crashes/hangs continue

---


---
title: "Ubuntu 12.10 w/ AMD Radeon HD 6800 - various troubles"
date: 2013-03-02
forum: Multimedia Software
---

### Post by fdepaola on 2013-03-02
Hi all. I am having a few problems, all of which I think involve my graphics card driver.
My setup is a dual-boot Windows 7/Ubuntu 12.10, currently using the proprietary drivers, as selected from Software Sources->Additional Drivers. 
Grub works fine but when I choose to boot into Ubuntu, I get no Plymouth splash screen. Instead, I get a completely black screen for a few seconds with a blinking cursor underscore in the top left.
The other issue I noticed was when I attempted to run Team Fortress 2 from Steam (Linux native, not in WINE). Upon startup, I get only a black screen for less than 1 second before it returns to desktop. With FTL, I originally had the same problem until I switched to the driver I'm using now (from the open source Xorg driver, I believe).

Now, a lot of tutorials ([this is the one I'm currently trying]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/129200#129200")) I've seen on getting the right driver for this setup include the step "sudo sh /usr/share/ati/fglrx-uninstall.sh" before installing the new driver, but my system doesn't seem to have a file called fglrx-uninstall.sh. So I continued the steps until the installer ran and told me that I already have a previous install of the fglrx driver. What can I do about this if I don't have the fglrx-uninstall.sh? What are potential negative consequences of installing with --force?

Thanks in advance.

---

### Post by fdepaola on 2013-03-02
PS. Here is the output from terminal when I try to run TF2, in case it's of value.

> Game update: AppID 440 "Team Fortress 2", ProcID 2499, IP 0.0.0.0:0
ERROR: ld.so: object 'gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded: ignored.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.

(steam:2167): LIBDBUSMENU-GLIB-WARNING **: Trying to remove a child that doesn't believe we're it's parent.
SDL video target is 'x11'
SDL video target is 'x11'
This system supports the OpenGL extension GL_EXT_framebuffer_object.
This system supports the OpenGL extension GL_EXT_framebuffer_blit.
This system supports the OpenGL extension GL_EXT_framebuffer_multisample.
This system DOES NOT support the OpenGL extension GL_APPLE_fence.
This system DOES NOT support the OpenGL extension GL_NV_fence.
This system supports the OpenGL extension GL_ARB_sync.
This system supports the OpenGL extension GL_EXT_draw_buffers2.
This system supports the OpenGL extension GL_EXT_bindable_uniform.
This system DOES NOT support the OpenGL extension GL_APPLE_flush_buffer_range.
This system supports the OpenGL extension GL_ARB_map_buffer_range.
This system supports the OpenGL extension GL_ARB_vertex_buffer_object.
This system supports the OpenGL extension GL_ARB_occlusion_query.
This system DOES NOT support the OpenGL extension GL_APPLE_texture_range.
This system DOES NOT support the OpenGL extension GL_APPLE_client_storage.
This system DOES NOT support the OpenGL extension GL_ARB_uniform_buffer.
This system supports the OpenGL extension GL_ARB_vertex_array_bgra.
This system supports the OpenGL extension GL_EXT_vertex_array_bgra.
This system supports the OpenGL extension GL_ARB_framebuffer_object.
This system DOES NOT support the OpenGL extension GL_GREMEDY_string_marker.
This system DOES NOT support the OpenGL extension GL_ARB_debug_output.
This system supports the OpenGL extension GL_EXT_direct_state_access.
This system DOES NOT support the OpenGL extension GL_NV_bindless_texture.
This system supports the OpenGL extension GL_AMD_pinned_memory.
This system DOES NOT support the OpenGL extension GL_EXT_framebuffer_multisample_blit_scaled.
This system supports the OpenGL extension GL_EXT_texture_sRGB_decode.
This system DOES NOT support the OpenGL extension GL_NVX_gpu_memory_info.
This system supports the OpenGL extension GL_ATI_meminfo.
This system supports the OpenGL extension GL_EXT_texture_compression_s3tc.
This system DOES NOT support the OpenGL extension GLX_EXT_swap_control_tear.
GL_NV_bindless_texture: DISABLED
GL_AMD_pinned_memory: DISABLED
GL_EXT_texture_sRGB_decode: AVAILABLE
Installing breakpad exception handler for appid(gameoverlayui)/version(20130224234706_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0_client)
saving roaming config store to 'sharedconfig.vdf'
roaming config store 2 saved successfully
Gtk-Message: Failed to load module "overlay-scrollbar"
[0302/172450:WARNINGroxy_service.cc(646)] PAC support disabled because there is no system implementation
Using breakpad crash handler
Setting breakpad minidump AppID = 440
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID: Caching Steam ID: 76561198006305252 [API loaded yes]
Steam_SetMinidumpSteamID: Setting Steam ID: 76561198006305252
Did not detect any valid joysticks.
GL_NVX_gpu_memory_info: UNAVAILABLE
GL_ATI_meminfo: AVAILABLE
GL_ATI_meminfo: GL_TEXTURE_FREE_MEMORY_ATI: Total Free: 881523, Largest Avail: 688128, Total Aux: 1752612, Largest Aux Avail: 640
GL_MAX_SAMPLES_EXT: 8
Gtk-Message: Failed to load module "overlay-scrollbar"
CShaderDeviceMgrBase::GetRecommendedConfigurationInfo: CPU speed: 3101 MHz, Processor: GenuineIntel
GlobalMemoryStatus: 4294967295
CShaderDeviceMgrBase::GetRecommendedConfigurationInfo: CPU speed: 3101 MHz, Processor: GenuineIntel
GlobalMemoryStatus: 4294967295
[0302/172451:ERROR:resource_bundle.cc(411)] Failed to load /home/tellisk/.local/share/Steam/SteamApps/tellisk/Team Fortress 2/cef_gtk.pak
Some features may not be available.
[0302/172451:WARNINGroxy_service.cc(646)] PAC support disabled because there is no system implementation
IDirect3DDevice9::Create: BackBufWidth: 1360, BackBufHeight: 768, D3DFMT: 3, BackBufCount: 1, MultisampleType: 0, MultisampleQuality: 0
/home/tellisk/.local/share/Steam/SteamApps/tellisk/Team Fortress 2/hl2.sh: line 72: 2505 Segmentation fault (core dumped) ${GAME_DEBUGGER} "${GAMEROOT}"/${GAMEEXE} "$@"
Game removed: AppID 440 "Team Fortress 2", ProcID 2505
saving roaming config store to 'sharedconfig.vdf'
roaming config store 2 saved successfully

---

### Post by fdepaola on 2013-03-06
Still working on these issues. Anyone have experience with similar?

---

### Post by fdepaola on 2013-03-14
Bump. If there's any more information I can provide please let me know.

---


---
title: "Display resolution issues while launching games after upgrading Ubuntu to 12.10"
date: 2012-12-05
forum: Multimedia Software
---

### Post by amitst on 2012-12-05
After upgrading to 12.10 I noticed that the games in full screen mode are not able to display properly.

After launching the fullscreen game (e.g. tremulous or openttd), I see only partial game screen on my monitor.

The regular desktop without the game launched looks just fine (I am on 1440x900 resolution but games run on lower resolutions like 800x600 or 640x480).

Any comments why this might be happening? Any solutions?

Here is my version in detail,
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

---

### Post by verzx on 2012-12-05
You got the latest Graphics card drivers etc? If not then that could be the solution.

---

### Post by amitst on 2012-12-05
I am not sure whether the drivers is the problem. I checked System Settings -> Details -> Graphics and I see "Intel® 945G x86/MMX/SSE2".

One more thing I noticed was I removed nearly all .* directories and files from my home directory once (except say the .tremulous) and all settings got reset and I was able to see the fullscreen graphics properly. So the drivers might be correct.

However, after playing few hours and doing various activities, the problem has resurfaced. I don't remember what has caused it to reappear. I don't want to remove all .* directories again.

---

### Post by amitst on 2012-12-05
Here is the output of "LIBGL_DEBUG=verbose glxinfo" command. It seems it can't read .drirc file. Is that an issue?

libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/i915_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/i915_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/amit/.drirc: No such file or directory.
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/amit/.drirc: No such file or directory.
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_multisample, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_get_proc_address, 
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) 945G x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 9.0
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    ...

---

### Post by amitst on 2012-12-05
I used another account and the game launched properly (though it didn't reset the resolution back to original after game exit). This means something wrong with my home directory content (related to settings). Any pointers?

---

### Post by amitst on 2012-12-08
The problem resurfaced after rebooting my machine.

I finally found the solution by installing "Gnome Shell" and using it instead of Unity Dash. Now the games are launching properly. Not sure why Unity wasn't able to set the resolution correctly.

---


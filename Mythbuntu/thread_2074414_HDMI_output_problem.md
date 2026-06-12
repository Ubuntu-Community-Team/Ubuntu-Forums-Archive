---
title: "HDMI output problem"
date: 2012-10-21
forum: Mythbuntu
---

### Post by mikitz on 2012-10-21
Hi everyone, I'm having issues getting HDMI output to work with Mythbuntu. It works great with VGA out to an LCD, but ultimately this is a HTPC that will be controlled with remote only on a Panasonic Viera 42" TV. This is on an ASROCK Z78M motherboard with VGA/HDMI/DVI outputs. I understand linux sees the DVI as another HDMI output (?)

The only way I am able to get HDMI out to TV working is if VGA is the only connection at bootup, then connect HDMI to TV after bootup, execute the command 'xrandr --auto' and viola, output to HDMI is perfect. But if HDMI is connected at bootup, it refuses to work, even with xrandr.

Anyone else experience this problem? A USB stick Mythbuntu would not show any HDMI output either. 

Any ideas or similar issues? I can post output for xrandr if it will help.

---

### Post by mikitz on 2012-10-21
Ok more weird behaviour:

- From grub if I select recovery mode, it freezes for a couple minutes and I have to press 'enter' (but I can't see the bottom output line due to monitor size) and then the system proceeds to load up the myth frontend fine on the TV with perfectly sized resolution.. 

This still isn't a solution since it takes >2 mins to boot due to the delay.. any ideas?

---

### Post by mikitz on 2012-10-21
I am just posting an update in hopes it will help someone else pinpoint a similar issue.. in recovery mode the last line before the delay is:

conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver

I followed the advice at [http://askubuntu.com/questions/169912/fb-conflicting-fb-hw-usage-inteldrmfb-vs-efi-vga-removing-generic-driver](http://askubuntu.com/questions/169912/fb-conflicting-fb-hw-usage-inteldrmfb-vs-efi-vga-removing-generic-driver)

about removing the line 'gfxmode $linux_gfx_mode' from grub but still get no HDMI output unless I use the recovery mode. Again, pressing enter (twice) after the error in recovery mode will load up everything fine, but I cannot see what the line below the 'removing generic driver' line is due to TV resolution.

Still stuck, but getting closer!

---

### Post by nickrout on 2012-10-21
Perhaps you should tell us what graphics adaptor you have, and what drivers you are using.

---

### Post by mikitz on 2012-10-21
Sorry about that, it is integrated HD graphics on a G630 processor using standard OpenGL drivers. Here some of the output from glxinfo:


name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_EXT_texture_from_pixmap
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20
OpenGL extensions:
[***At least 1 screen full of extensions are listed here***]



and output from xrandr...

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1920 x 1024
default connected 1024x768+0+0 0mm x 0mm
   1280x1024      61.0  
   1920x540        0.0  
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  
   1920x1024      61.0

---

### Post by mikitz on 2012-10-21
Ok I figured it out it required a change in the grub line.
I removed the line 'gfxmode $linux_gfx_mode'
and added 'nomodeset' to the end of the linux /boot/vmlinuz.. line
Now it boots without any errors and also quickly as it should.
Hopefully this helps someone else out there.
:guitar:

---


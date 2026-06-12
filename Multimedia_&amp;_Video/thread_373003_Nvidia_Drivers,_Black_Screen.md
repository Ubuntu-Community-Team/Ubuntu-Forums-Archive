---
title: "Nvidia Drivers, Black Screen"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by slamgauge on 2007-02-28
Running 6.10 with a Nvidia 6600GT.

I get a pitch black screen when the Ubuntu splash screen should be up after installing
the nvidia drivers and rebooting.  I have to revert to an old xorg.conf in order to get back
into a working X environment.  After looking through the two different xorg.conf files, the only noticeable difference between the two is the xorg.conf with "nv" works while the xorg.conf with "nvidia" as the driver does not.  

I have tried using Envy to install and I get the same problem.  

Any suggestions?

---

### Post by booe on 2007-03-02
Could you please:

a) let us know how you installed the NVIDIA drivers, did you follow a tutorial from these forums? did you use the NVIDIA installer and if so, which version?

b) inform us of if have you recently updated your kernel (by updating linux-* packages)? if so, this will always remove the proprietary drivers!

c) clarify whether "black screen" means totally black with nothing on the screen at all... or if you have a prompt/login request?

d) check /var/log/messages and /var/log/Xorg.0.log and /var/log/dmesg to see if any errors are showing up (regarding your last few broken boot-ups) that might explain your problem. If so, please post the output here so people can assist you better.

Thanks :)

---

### Post by articbones on 2007-03-04
I am having the same (it would appear) problems as the original poster.  I am a newbie, so please excuse any mistakes I make in terminology.

I first tried installing under the new Fiesty (Herd 5?), and that did not work (black screen).  I did not think it that reasonable for a newbie like me to expect to get this working, so I completely wiped my installation, then installed Edgy, then had the same problem.

My reason for installing (or trying to install) the driver was to get glx working.

I am not the original poster, but I will post my answers to booe's questions.  Hopefully that will help us get to the bottom of things.

> **booe said:**
> Could you please:

a) let us know how you installed the NVIDIA drivers, did you follow a tutorial from these forums? did you use the NVIDIA installer and if so, which version?

I used the installer from the NVIDIA web site.  The file was called "NVIDIA-Linux-x86-1.0-9746-pkg1.run".

To install, I flipped out to the command line (ctrl-alt-F1), then I killed my X11 stuff (sudo killall gdm), then I ran the installer (sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run).  I had to install "build-essential" to get the NVIDIA installer working (it needed header files or libraries or something).

> **booe said:**
> 
b) inform us of if have you recently updated your kernel (by updating linux-* packages)? if so, this will always remove the proprietary drivers!

I did update my kernel.  This was done by the automatic update facility.  I installed the NVIDIA driver after the kernel update though.

> **booe said:**
> 
c) clarify whether "black screen" means totally black with nothing on the screen at all... or if you have a prompt/login request?

For me, the black screen is entirely black, nothing at all.  Interestingly the keyboard does not seem to respond at all (I might expect to be able to ctl-alt-del maybe?), and turning on the caps lock does not work.

> **booe said:**
> 
d) check /var/log/messages and /var/log/Xorg.0.log and /var/log/dmesg to see if any errors are showing up (regarding your last few broken boot-ups) that might explain your problem. If so, please post the output here so people can assist you better.

No errors that I can see.

Edit:  I am using a GeForce 6600 GT

Thanks

---

### Post by peebly on 2007-03-04
Using fiesty

On early version of fiesty, I had a problem with a blank screen after boot.

[PHP]sudo apt-get install nvidia-glx

sudo nvidia-xconfig --add-argb-glx-visuals --composite[/PHP]

Then press at the same time Ctrl - Alt - Backspace, to restart X.

On fiesty this got things going, for me anyway.

Never tried it with Edgy.

---

### Post by articbones on 2007-03-04
> **peebly said:**
> Using fiesty

On early version of fiesty, I had a problem with a blank screen after boot.

[PHP]sudo apt-get install nvidia-glx

sudo nvidia-xconfig --add-argb-glx-visuals --composite[/PHP]

Then press at the same time Ctrl - Alt - Backspace, to restart X.

On fiesty this got things going, for me anyway.

Never tried it with Edgy.

Cheers peebly.  I tried that just now; the screen goes black with a flashing cursor in the top-left corner, then it goes completely black (like before).

---

### Post by articbones on 2007-03-04
OK, I flattened my machine and reinstalled Edgy.  I then used the Envy tool to install the NVIDIA driver.  I did not install any updates or other software before the driver, so this is a completely clean system.

I still have the same problem, but now when I look at the /var/log/Xorg.0.log it has this:

```
(EE) AIGLX: Screen 0 is not DRI capable
```

(I might have missed this before)

and

```

(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
```

The second message is present even with the non-proprietary "nv" driver.  There is also some garbage about /dev/wacom devices, but that seems to be there whatever configuration I use.

---

### Post by slamgauge on 2007-03-04
> **booe said:**
> Could you please:

a) let us know how you installed the NVIDIA drivers, did you follow a tutorial from these forums? did you use the NVIDIA installer and if so, which version?

b) inform us of if have you recently updated your kernel (by updating linux-* packages)? if so, this will always remove the proprietary drivers!

c) clarify whether "black screen" means totally black with nothing on the screen at all... or if you have a prompt/login request?

d) check /var/log/messages and /var/log/Xorg.0.log and /var/log/dmesg to see if any errors are showing up (regarding your last few broken boot-ups) that might explain your problem. If so, please post the output here so people can assist you better.

Thanks :)

A. I used the guide found here [http://ubuntuforums.org/showthread.php?t=301499]("http://ubuntuforums.org/showthread.php?t=301499")
B. No updates, this is a new install.
C. The black screen is totally black. No prompt.  It is as if the monitor was not connected.
D. I am afraid I am a noob and would not be able to recognize errors.  I looked through those files but I assume since I have reverted to an old working xorg.conf that those files are associated to the working boot and not the broken boot.

---

### Post by tmottabr on 2007-03-08
Im having the same problem. i own a Dell Latitude D840 notebook with a builtin nvidia geForce4 440 Go.

I installed the new Herd5 from the alternate CD, upgraded everything trought the command:

sudo aptitude upgrade
sudo aptitude dist-upgrade

installed the 386 kernel

sudo aptitude install linux-image-2.6.20-8-386

then installed the nvidia driver

sudo aptitude install nvidia-glx

when i change the drive from NV to NVIDIA in the xorg.conf the gdm starts all black, and by black i mean totally black, nothing comes up. But by my speaker comes the sound that normally the system do when finish loading. So i guest that all is working, just my video card that is not.

if i change back to NV the gdm comes nice and clear.

i dont checked the error log. will do now and post here.

Reggards,

---

### Post by tmottabr on 2007-03-08
As i said, i checked the log, but no error was found.

i tried remove the nvidia-glx and install the nvidia-glx-legacy but then i get the error informing that the kernel version of the module was 9631 and the x version of the module is 7184 and the X dont even start.

---

### Post by maccabbi on 2007-03-09
I had the same problem but running sudo dpkg-reconfigure xserver-xorg and chose nv and which resolutions I needed. After that it was okay

---

### Post by tmottabr on 2007-03-09
I dont want to use the built-in NV driver, i want to use the NVIDIA driver.

I made some tests with the linux-image-2.6.20-8-386, linux-image-2.6.20-9-386 and linux-image-generic, always the same problem.

After that, i was geting the updates from br.archive.ubuntu.com (im in brazil). So i swaped to the main site, i hade several new updates to install, but when i finished the problem remains.

I read in some place that this is a problem in the version 9631 of the driver, maybe is not the time to update it since the version 9755 was alread released?

---

### Post by tato626 on 2007-03-15
hi!

Sorry for my bad english!

I have the same problem: totally black screen before login.
I can initiate my session when push Crtl+Alt+Del (when I press that keys the Splash Screen starts perfect :confused: )
If I don't press that keys the screen is always black and the mouse appears as load...

For me isn't very seriously bug (at moment) but I am worried.

I use Feisty+Beryl with the latest nvidia drivers, but the problem appeared last night  when I restart the session and when everything was working well...

Someone idea?

---

### Post by mateus109 on 2007-03-22
I too am having problems with an all black screen when installing the nVidia drivers on a Geforce4 440 Go.

I've installed the 9631 drivers and followed instructions from many websites (including the nVidia driver installation manual) but I always get a black screen.

A year ago I was running Mandrake on my laptop & had no problems getting the nvidia drivers working; so is it to do with the newer nvidia releases?

I'm running a Dell Inspiron 8200 with a 64mb Geforce4 440 Go.

Thanks.

[RIGHT][/RIGHT];)

---

### Post by ojah on 2007-03-24
Same here.
Feisty on an Inspiron 8200 with that geforce 440 go.
Played alot with xorg.conf to no avail. Getting a (real) black screen with nvidia-glx driver instead of the login screen, whereas nv (2d) driver works ok.
Edgy worked fine on the same hardware.

---

### Post by ojah on 2007-03-25
Just for the records real quick:
In order to get a geforce 4/mx/go (may other older nvidias as well)
run 3d (without that show stopping black screen;) : 
apt-get remove nvidia-glx
apt-get install nvidia-glx-legacy

This goes for my good ole Inspiron 8200 with a gf440 go.

---

### Post by mateus109 on 2007-03-25
Ok I got it working now.

I removed & reinstalled the drivers following instructions from this forum.  Must have missed something the first time around or I added an option that the graphics card didn't like.

Got Beryl working too. :)

---

### Post by Theimon on 2007-03-25
I've been having this same problem with Dapper, Edgy and currently on Feisty as well. My initial Dapper install (on a nVidia 6600) worked great with the standard nvidia-glx driver. But then sometime the kernel got an upgrade and since then (approx. 9 months or so) every install I try, the nVidia driver fails. All installation methods (aptitude, Envy script, direct binary nVidia package) result in the same error. At the point where the nVidia splash should show up, the screen goes black and the system becomes nonresponsive.
At this point, I did a fresh clean Feisty install. I pulled in the initial updates, but didn't touch anything else. I installed nvidia-glx through Synaptic, set the driver to nvidia in xorg.conf, rebooted and errored out. A hard reset is my only option, then adjust the driver to nv and then it all starts fine. But since I want full 3D support, I want the nVidia driver to work.
I checked the Xorg.log and I can see that everything gets loaded properly. It loads the right modules, the right driver, etc. etc. I have no exotic settings in the xorg.conf, but still I get a black screen.
Are there any options left????

---

### Post by form51 on 2007-03-25
I have the same EXACT problem with a BFG 6600 GT.. I'll be keeping an eye on this thread :]

---

### Post by flusheDData on 2007-03-27
Hi,
for thoese who do not want the binary but to compile the Nvidia site's driver which works well on GeForce4 440 Go (Dell Inspiron 8200) try this:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run)
The 96xx would give you a black screen.
Regards,
Flush

---

### Post by Theimon on 2007-03-27
> **flusheDData said:**
> Hi,
for thoese who do not want the binary but to compile the Nvidia site's driver which works well on GeForce4 440 Go (Dell Inspiron 8200) try this:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run)
The 96xx would give you a black screen.
Regards,
Flush

I don't want to go back tons of driver versions, this system should be able to use the newer drivers, or at least 1 version prior to the newest. (actually, the 8776 gives me the same bloody error.)
No luck so far with searching on the nvnews.net forums......the quest isn't finished yet :(

---

### Post by Theimon on 2007-03-27
Eureka!!!!......wait, let me say that again...........EUREKA!!!!

I was going through woods of wiki. google, you name it.......with foam at the mouth I tried stuff and failed, BUT........!!

I found the answer and it is as follows:
_NOTE: this is for AGP systems!!_

Apparently when booting your system and loading the nvidia module, the system can't decide which AGP module to load, since it can choose between two or three of those (agpgart, nvidia_agp, amd64_agp (in my case))
So you have to force the nvidia_agp by doing the following:
Add:```
Option         "NvAGP" "1"
``` to the device section of your xorg.conf so it will end up looking like this:
```

Section "Device"
    Identifier     "nVidia Corporation N43 [GeForce 6600]"
    Driver         "nvidia"
    Option         "NvAGP" "1"
EndSection

```
When I added this, I rebooted the system and expected to see another perpetual black screen. Instead it showed me a nice Nvidia splash logo and right after that it gave me the gdm login prompt.
"glxgears -info" works and "glxinfo" now tells me this:
```
GL_RENDERER   = GeForce 6600/PCI/SSE2/3DNOW!
GL_VERSION    = 2.1.0 NVIDIA 97.55
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
16576 frames in 5.0 seconds = 3315.069 FPS
16499 frames in 5.0 seconds = 3299.667 FPS
16481 frames in 5.0 seconds = 3296.089 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 39 requests (39 known processed) with 0 events remaining.
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 39 requests (39 known processed) with 0 events remaining.
theimon@know-where-to-run:~$ sudo gedit /etc/X11/xorg.conf
Password:
theimon@know-where-to-run:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.0 NVIDIA 97.55
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x42 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x46 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x4a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5d 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x61 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x65 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x69 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6d 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x154 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

How you like them apples!?

As I said this (in my eyes) should only work for AGP systems, so if you're on a PCI-E card, try to find something similar or keep on searching. But if you're on an AGP card, give it a try, it can't get any worse, it can only get better.
Cheers!

---

### Post by form51 on 2007-03-27
Thank you Theimon.

I unfortunately do have a PCI-E card.. :/  haha .. but this may give me some where to start.. I will update the thread if I make any progress.

---

### Post by NewJack on 2007-03-29
Excuse me for being a n00b, I want to try Theimon's fix but when I load up I can't get past the black screen.  If I load into recovery mode, how do I get to where I can make those changes and restart?  I am currently running Dapper.

Thanks!

---

### Post by Theimon on 2007-03-29
> **NewJack said:**
> Excuse me for being a n00b, I want to try Theimon's fix but when I load up I can't get past the black screen.  If I load into recovery mode, how do I get to where I can make those changes and restart?  I am currently running Dapper.

Thanks!

Boot your system into recovery mode, when you get to the command prompt, typ:
```
nano /etc/X11/xorg.conf
``` (note the capital X, you HAVE to enter that exactly)

When you've entered that, you'll get your xorg.conf in front of you. Enter the appropriate changes, hit "Ctrl+X", hit the "Y" button, hit "Enter" and then reboot your system. Not specifically necessary, but you'll be sure it will load all the right modules. Then sit back and keep your fingers crossed.

Edit: to reboot your system from the command line typ: ```
shutdown -r now
```

---

### Post by form51 on 2007-03-30
He'll probably need to write sudo before nano.

I still can't get mine working :(

---

### Post by Theimon on 2007-03-30
> **form51 said:**
> He'll probably need to write sudo before nano.

I still can't get mine working :(

Not when you're in recovery mode, then you're already root from the start.

---

### Post by idryl on 2007-04-03
Hello everyone.

I thought I'd add my experience...


I've got a Nvidia MX 4000 AGP which is quite an old card, so I was using the 7184 version of the Nvidia driver, as this is marked as "legacy" on their website.

I too experienced the blank screen and had no option but to reboot and restore my old xorg.conf file.

However... I noticed that actually my card is supported by a newer version of the Nvidia driver (96xx) but not by the latest (97xx) ones. So I installed the 9631 driver and it all works now, yay. No more blank screens :grin: 


Another step I took that may have helped was to install a different version of the NVidia kernel headers, previously I had the "nvidia-kernel-source" package installed but I changed that to "nvidia-legacy-kernel-source".


-David

---

### Post by Theimon on 2007-04-19
Bumping an old thread for future reference and maybe some help for others:

My solution was just a temporary half working it seems now after a few weeks. But I did find the conflict in the system. Apparently the i2c modules which get loaded with nvidia and agpgart made every distro I installed see the AGP card as a PCI: hence no AGP acceleration.
So I booted my system, opened a terminal and entered: ```
lsmod|grep i2c
```
Then I opened another terminal, typed: ```
sudo nano /etc/modprobe.d/blacklist
``` and copied over the exact i2c modules the first command gave me.
I commented out all AGP related options in my xorg.conf, rebooted my system and hoped for the best.
When it came back up, I saw the nVidia splash. In nvidia-settings I could see the system now recognized my card as AGP 8x, and when doing ```
cat /proc/driver/nvidia/agp/*
``` it showed me AGP was enabled at 8x using the agpgart driver.
Hope maybe this will help someone.

---

### Post by Huffalump on 2007-04-20
Thanks for your effort.  

Unfortunately, this did not solve my problem.  I do have an AGP card (GeForce FX 5600).

I was working just perfectly fine in Edgy, then ill-advisedly upgraded to Fiesty and have not been able to get X working ever since.  There's a thousand solutions and ideas on the forums, but none of them seem to work.

"Failed to load module wfb"

Just wanted to leave some feedback for you, as I tried adding that Option to the conf but it did not fix me.

---

### Post by Theimon on 2007-04-20
> **Huffalump said:**
> Thanks for your effort.  

Unfortunately, this did not solve my problem.  I do have an AGP card (GeForce FX 5600).

I was working just perfectly fine in Edgy, then ill-advisedly upgraded to Fiesty and have not been able to get X working ever since.  There's a thousand solutions and ideas on the forums, but none of them seem to work.

"Failed to load module wfb"

Just wanted to leave some feedback for you, as I tried adding that Option to the conf but it did not fix me.

The wfb problem only occurs with the newest driver (9755) as far as I know, maybe try the 9631. The wfb module is only there for the GF8*** series, but it seems even if you don't own a 8*** series the system still needs that module to be there. 
So, like I said, try an earlier version, block the i2c modules and boot it up. I'm running the 9631 as we speak and it's working like a charm.

---

### Post by Theimon on 2007-04-21
Just a note on the side. I tested the "i2c-solution" on both Dapper and Feisty. They both work flawlessly.

---

### Post by adewale on 2007-04-21
am not sure if am supposed to post my problem here but it seems a little bit different. I have an nvidia mx 400 i have tried a lot of drivers but they freeze my pc and it seems am the only person suffering this issue now my media player amarok wont load is there anyway i can overcome this issues thanks

---

### Post by blaznlion on 2007-05-26
I too am having problems with the nvidia-glx drivers for my Dell Inspiron 8200 with a Geforce4 440 MX card.  Has there been a clean cut solution to this issue yet or at least a work around?  I am able to work using 'nv' driver but would really like to be able to use the nvidia-glx drivers.

---

### Post by Nehvrook on 2007-06-07
> **Theimon said:**
> Eureka!!!!......wait, let me say that again...........EUREKA!!!!

I was going through woods of wiki. google, you name it.......with foam at the mouth I tried stuff and failed, BUT........!!

I found the answer and it is as follows:
_NOTE: this is for AGP systems!!_

Apparently when booting your system and loading the nvidia module, the system can't decide which AGP module to load, since it can choose between two or three of those (agpgart, nvidia_agp, amd64_agp (in my case))
So you have to force the nvidia_agp by doing the following:
Add:```
Option         "NvAGP" "1"
``` to the device section of your xorg.conf so it will end up looking like this:
```

Section "Device"
    Identifier     "nVidia Corporation N43 [GeForce 6600]"
    Driver         "nvidia"
    Option         "NvAGP" "1"
EndSection

```
When I added this, I rebooted the system and expected to see another perpetual black screen. Instead it showed me a nice Nvidia splash logo and right after that it gave me the gdm login prompt.

How you like them apples!?

As I said this (in my eyes) should only work for AGP systems, so if you're on a PCI-E card, try to find something similar or keep on searching. But if you're on an AGP card, give it a try, it can't get any worse, it can only get better.
Cheers!



I could kiss you! Thank you. Probelm solved :D

---

### Post by blaznlion on 2007-06-13
I figured out how to get my NVIDIA driver to work.  I added this to the Screen Section
```
Option "UseDisplayDevice" "DFP"
```

---

### Post by TomCat39 on 2007-08-22
Hey guys, I guess I'm more newb than all of you.

I see everyone saying they have gotten a black screen. Some with sound of full boot and some without.

And I see every single one says they reverted to old conf file or drivers or whatnot.

My question, is how in the world did you do this when you can't see anything aka a black screen?

I found I can finally get to the hard drive via Live CD I downloaded onto my windoze machine and burned. But even there I cant mount the drive via sudo mount /dev/sda

I have to goto the GUI administrative/drive utility and select the partition and "make accessible"

If I do it via command line or terminal with sudo, I get an error that it can't be found to be mounted.

Once I use the admin/drives utility, it tells me it's already mounted via command line.

Also note, this is the LTS dapper drake version I fubarred by trying one of the methods on the NVidia dapper wiki. 

Also note, I can boot with this Geforce 8800 GTS via live CD and Safe Graphical. But regular boot via CD or HD comes up black screen.

Hitting CTRL-ALT-DEL starts service shutdown and a reboot after a minute or so. CTRL-ALT-Backspace does nothing.

How can I get back to my native HD install command line when it doesn't finish booting, just goes to a black screen and sits there indefinitely? No boot music for Ubuntu Log In or anything.

Is there a way to choose "Safe Graphical" boot on the HD install or is that purely the Live CD.

I've been reading forum post after forum post and tried following the directions on the wiki but I ended up making things worse. 

At least before I tried installing any drivers Xserver failed with an error that it couldn't initialize the GUI and would let me drop to the command line. That's where I tried method 1 of the Dapper Drake NVidia wiki and got to step 6 before hitting an error concerning the gksudo gedit step. Gave me an error {0691} or something of the like. Was yesterday so don't recall the number displayed now.

Anyways, if someone could tell me how to get back to be able to dinker with the file system, without reinstalling the OS. That would be great.

Or is it hooped being all I get is a black screen?

---

### Post by tseliot on 2007-08-22
> **TomCat39 said:**
> My question, is how in the world did you do this when you can't see anything aka a black screen?
Boot in Recovery Mode (select it from the GRUB menu)

then type:
```
sudo dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot
```

and boot as usual

[QUOTE=TomCat39;3232329]At least before I tried installing any drivers Xserver failed with an error that it couldn't initialize the GUI and would let me drop to the command line. That's where I tried method 1 of the Dapper Drake NVidia wiki and got to step 6 before hitting an error concerning the gksudo gedit step. Gave me an error {0691} or something of the like. Was yesterday so don't recall the number displayed now.
you can launch gedit if the Xserver is disabled. You can use "nano", etc. instead

---

### Post by TomCat39 on 2007-08-22
> **tseliot said:**
> [QUOTE=TomCat39;3232329]My question, is how in the world did you do this when you can't see anything aka a black screen?
Boot in Recovery Mode (select it from the GRUB menu)

then type:
```
sudo dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot
```

and boot as usual


you can launch gedit if the Xserver is disabled. You can use "nano", etc. instead

Okay, sounds good. But what keys do I press to get the GRUB menu so as to boot in recovery mode?

Everything I've been doing is via instructions from here. It's not from my own knowledge, even though I have been learning lots from this adventure. :D

---

### Post by tseliot on 2007-08-22
> **TomCat39 said:**
> [QUOTE=tseliot;3232463]

Okay, sounds good. But what keys do I press to get the GRUB menu so as to boot in recovery mode?

Everything I've been doing is via instructions from here. It's not from my own knowledge, even though I have been learning lots from this adventure. :D
Turn on your computer, then, after the BIOS screen, you should see some writings about a countdown. Press your "Down" (keyboard) arrow (before time is up) and you will be able to select Recovery mode.

---

### Post by TomCat39 on 2007-08-22
> **tseliot said:**
> [QUOTE=TomCat39;3234455]
Turn on your computer, then, after the BIOS screen, you should see some writings about a countdown. Press your "Down" (keyboard) arrow (before time is up) and you will be able to select Recovery mode.
Wonderful. Thank you very much for that tidbit of info. That was the key I was missing. 

Now I can go about working on the system.

Thank you. 

I'm sure I'll check back with more questions later.

---

### Post by TomCat39 on 2007-08-23
Okay I've reverted back to the VESA no-3d drivers and the desktop comes up and all is well.

So I recall reading that the restricted nvidia glx drivers must be removed before the latest NVidia Linux drivers can be built.

So I check the advance portion of the Synaptic Package manager and sure enough the restricted NVidia glx drivers are installed. I'm assuming that the onboard video is an NVidia integrated video chip. I didn't set up this Ubuntu Distro but am learning quickly none the less.

So I find the instructions on how to remove the necessary items via command line after stopping the GDM:

```
cd ~/Desktop
sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo rm /etc/init.d/nvidia-*
sudo apt-get install fakeroot build-essential linux-headers-amd64-generic linux-headers-generic gcc pkg-config xserver-xorg-dev linux-headers-`uname -r`
sudo sh NVIDIA-Linux-x86_64-100.14.09-pkg2.run
sudo nvidia-xconfig --no-composite
```

Except I use the x386-pkg1.run file to fit my GF's machine.

All seems to go well except I'm never ask to continue or anything on the removal of the packages. Just said something about selected packages it found then gave me the command line. so I went to the rm (remove) nvidia-* files. And went with the sh run file command. I had already downloaded my headers through the package manager. I do the --no-composite bit and reboot.

The error Xserver gave is that the version driver is the 100.14.11 but the NVidia kernel Module doesn't match.

Why didn't the purge actually purge?

When I checked the NVidia glx and the restricted modules in the package manager for removal it said it wanted to remove all kinds of things. Looked to me like it wanted to remove gnome desktop and all so I opted out and didn't go that route. I just want to remove the items preventing the drivers from building correctly.

All that is in the machine is onboard ethernet/rj45, a stick of 512Meg DDR or DDR2 memory, 1 SATA drive, 1 DVD/CDrom and one 3.5 floppy. Do I need anything from the restricted driver module with that hardware? It's a dell prebuilt that we've added a EVGA Geforce 8600 GTS too so she can 3d game hoepfully.

Oh and for any fresh eyes, this is on Dapper Drake kernel fully updated with the latest updates.

Thanks again for all the help. This is a wonderful community.

---

### Post by tseliot on 2007-08-23
If you want you can try Envy (**at your own risk**):
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

follow point B of the instructions (otherwise it won't work for you):
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by TomCat39 on 2007-08-23
That's okay.

I don't know why this Install of Dapper Drake acts a little funny. Esc for grub menu not down arrow, purge fails to purge etc etc.

Anyways, I was paranoid that the restricted drivers for Linux had something we needed but after further inspection it's only for Video and some specialty cards FCUSB or something of the like.

So I used the Synaptic Package manager and removed all restricted drivers and all references of NVidia except the dimmer control. ran the NVIDIA.run file. Let it do everything. Rebooted and all worked like a charm. She is now getting 200 fps in Sauerbraten (Cube 2) for Linux.

I reinstalled the NVidia Control utility and it recognizes the new drivers and works like a charm.

So to all of you who may be trying to install a new NVidia card. You must remove the restricted  drivers from your distro or the drivers won't compile properly. 

I had only found 1 post talking about it so I thought having another say the same thing might be helpful in the forum searches we do. :D

And once again, thank you everyone for all the help, past and present. I wouldn't have been able to figure all this out if it weren't for you all.

Tomas

---

### Post by pkarlos_76 on 2007-08-24
> **Theimon said:**
> Eureka!!!!......wait, let me say that again...........EUREKA!!!!

I was going through woods of wiki. google, you name it.......with foam at the mouth I tried stuff and failed, BUT........!!

I found the answer and it is as follows:
_NOTE: this is for AGP systems!!_

Apparently when booting your system and loading the nvidia module, the system can't decide which AGP module to load, since it can choose between two or three of those (agpgart, nvidia_agp, amd64_agp (in my case))
So you have to force the nvidia_agp by doing the following:
Add:```
Option         "NvAGP" "1"
``` to the device section of your xorg.conf so it will end up looking like this:
```

Section "Device"
    Identifier     "nVidia Corporation N43 [GeForce 6600]"
    Driver         "nvidia"
    Option         "NvAGP" "1"
EndSection

```
When I added this, I rebooted the system and expected to see another perpetual black screen. Instead it showed me a nice Nvidia splash logo and right after that it gave me the gdm login prompt.
"glxgears -info" works and "glxinfo" now tells me this:
```
GL_RENDERER   = GeForce 6600/PCI/SSE2/3DNOW!
GL_VERSION    = 2.1.0 NVIDIA 97.55
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
16576 frames in 5.0 seconds = 3315.069 FPS
16499 frames in 5.0 seconds = 3299.667 FPS
16481 frames in 5.0 seconds = 3296.089 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 39 requests (39 known processed) with 0 events remaining.
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 39 requests (39 known processed) with 0 events remaining.
theimon@know-where-to-run:~$ sudo gedit /etc/X11/xorg.conf
Password:
theimon@know-where-to-run:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.0 NVIDIA 97.55
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x42 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x46 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x4a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4b 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5a 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5d 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x61 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x65 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x69 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6d 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x154 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

How you like them apples!?

As I said this (in my eyes) should only work for AGP systems, so if you're on a PCI-E card, try to find something similar or keep on searching. But if you're on an AGP card, give it a try, it can't get any worse, it can only get better.
Cheers!

Do you know how to solve this for PCI Expre3ss cards?

---

### Post by tseliot on 2007-08-24
> **pkarlos_76 said:**
> Do you know how to solve this for PCI Expre3ss cards?
try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by TomCat39 on 2007-08-24
> **pkarlos_76 said:**
> Do you know how to solve this for PCI Expre3ss cards?
I'm not really sure what you are asking, the card I just installed into my GF's machine was 8800 GTS which only comes in PCIe....

I just used the 100.14.11 driver package for my system build (x386) and it worked no problem.

The biggest thing is to remove the Linux Restricted Driver package prior to install or it will compile the wrong driver for the kernel. You also nead to make sure to have your kernel headers and any other thing the installer says you don't have.

Remember, you can always switch back to "VESA" to install more packages the installer for NVIDIA wants. You can do this until the installer is satisfied.

The driver works really well but you must provide it the proper tools to do it's job. And having any other NVidia drivers installed will just confuse the installer as to which driver to build the kernel layer from.

Good luck and let us know how you make out.

---

### Post by pkarlos_76 on 2007-08-24
> **TomCat39 said:**
> I'm not really sure what you are asking, the card I just installed into my GF's machine was 8800 GTS which only comes in PCIe....

I just used the 100.14.11 driver package for my system build (x386) and it worked no problem.

The biggest thing is to remove the Linux Restricted Driver package prior to install or it will compile the wrong driver for the kernel. You also nead to make sure to have your kernel headers and any other thing the installer says you don't have.

Remember, you can always switch back to "VESA" to install more packages the installer for NVIDIA wants. You can do this until the installer is satisfied.

The driver works really well but you must provide it the proper tools to do it's job. And having any other NVidia drivers installed will just confuse the installer as to which driver to build the kernel layer from.

Good luck and let us know how you make out.

I'm looking for the equivalent to Option "NvAGP" "1" for PCIE, but I'm getting the feeling this is a major bug in the nvidia drivers. I've tried nvidia's script, Kano's (kanotix) script, and I've tried envy, and it was envy that finally able to compile a nvidia driver that would load, with the exception of getting a black screen, in otherwards no video output, however the sound works, and if I blindly type in my password and username the system logs in even though I have no picture.

---

### Post by tseliot on 2007-08-24
> **pkarlos_76 said:**
> I'm looking for the equivalent to Option "NvAGP" "1" for PCIE, but I'm getting the feeling this is a major bug in the nvidia drivers. I've tried nvidia's script, Kano's (kanotix) script, and I've tried envy, and it was envy that finally able to compile a nvidia driver that would load, with the exception of getting a black screen, in otherwards no video output, however the sound works, and if I blindly type in my password and username the system logs in even though I have no picture.
try either point 16 of the Problems Section:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION)

or add this line to the Section Screen of your /etc/X11/xorg.conf :
```
Option "UseDisplayDevice" "DFP"
```

---

### Post by pkarlos_76 on 2007-08-24
> **tseliot said:**
> try either point 16 of the Problems Section:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION)

or add this line to the Section Screen of your /etc/X11/xorg.conf :
```
Option "UseDisplayDevice" "DFP"
```


I found the solution, which is odd and practical......my DVI cable was plugged into the 2nd DVI port on the video card, so I then plugged it into the first DVI port. ANd rebooted. Seems it was showing up as a VGA CRT-0 connected prior to this....basically a fake monitor. The solution I found was the system was showing a fake monitor in the Xorg.0.log, so I switched my DVI cable from the 2nd DVI port to the 1st DVI port on the video card and I got my desktop back, the 2nd DVI port was working find under vesa drivers, but doesn't seem to work under nvidia drivers for me. It is possible to use override statements too,but changing connector is more easy.

---


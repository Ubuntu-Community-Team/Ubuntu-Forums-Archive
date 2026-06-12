---
title: "Enabling Intel HD graphics for hardware decoding"
date: 2012-10-22
forum: Mythbuntu
---

### Post by mikitz on 2012-10-22
Hi there,

I have Mythbuntu 12.04 working fine except for enabling the Intel HD graphics GPU. While tuning OTA channels both processors almost max out. The processor is a Pentium G630 (dual core)

lspci | grep VGA gives

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

vainfo gives an error:

libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit


glxinfo gives

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
OpenGL version string: 2.1 Mesa 8.0.4
OpenGL shading language version string: 1.20
OpenGL extensions: 
(...etc)

Anything look off?
Thx in advance

---

### Post by mikitz on 2012-10-23
Ok how about a different question.. does anybody have Intel HD hardware (Sandy Bridge) working with VAAPI in Mythbuntu 0.25? I've tried the glasen ppa and x-edgers ppa and neither resolve the vainfo issue. 

Is it easier to start with a full Ubuntu distro and install mythbuntu after VAAPI is working? Or would it be easier to just go out and buy a $40.00 NVIDIA card and use VDPAU?

Thanks, I'm kind of lost!

---

### Post by nickrout on 2012-10-23
> **mikitz said:**
> Ok how about a different question.. does anybody have Intel HD hardware (Sandy Bridge) working with VAAPI in Mythbuntu 0.25? I've tried the glasen ppa and x-edgers ppa and neither resolve the vainfo issue. 

Is it easier to start with a full Ubuntu distro and install mythbuntu after VAAPI is working? Or would it be easier to just go out and buy a $40.00 NVIDIA card and use VDPAU?

Thanks, I'm kind of lost!
$40 would be well spent!

---

### Post by mikitz on 2012-10-23
Thx for the reply nickrout. It's nice to know there are others out there! 

I'll be using the machine for 2 ATSC tuners (channels are broadcast in 1080p I believe) The local computer shop has NVIDIA Silent GE Force 210 cards for cheap, also GT 430 cards for a bit more. The official mythtv site recommends the 8-series. I wish there were more reports in the hardware section. Anyone know if the GE Force 210 or GT 430 cards would be able to handle 2 decoding streams at once without any jitters?

---

### Post by nickrout on 2012-10-23
> **mikitz said:**
> Thx for the reply nickrout. It's nice to know there are others out there! 

I'll be using the machine for 2 ATSC tuners (channels are broadcast in 1080p I believe) The local computer shop has NVIDIA Silent GE Force 210 cards for cheap, also GT 430 cards for a bit more. The official mythtv site recommends the 8-series. I wish there were more reports in the hardware section. Anyone know if the GE Force 210 or GT 430 cards would be able to handle 2 decoding streams at once without any jitters?you won't be decoding two streams at once, unless you want to connect the machine to two tv's and running two frontends (not recommended). Decoding is only needed on watching, not recording.

The 210 is underpowered, the 430 is reportedly good. Take a look on the mailing list for recent discussions of the 5xx and 6xx series.

8xxx is out of date.

---

### Post by mikitz on 2012-10-23
Hey Nickrout, thanks for the suggestion. I am new to HTPC's, but the mailing list is a huge goldmine of info!! I've got some reading ahead of me for sure. For those who don't know of the mailing list.. 
[http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)

---

### Post by mikitz on 2012-10-25
If anyone else is having issues getting Intel HD graphics to work with Mythbuntu, I've done some research and it looks like either the NVIDIA GT430 or GT620 is the sweet spot between performance and power consumption for an HTPC. Anything less is reported to have a jittery picture at 1080p (like the GT 210). Another interesting thing I've discovered is the GT620 is just a rebranded GT430 with almost identical specs. Strange naming conventions, but good to know anyhow.

---

### Post by Linuxisfast on 2012-10-25
vaapi works fine here, I installed libva-intel-vaapi driver and vainfo returns all the valid points for h/w decoding. VLC runs fine with minimal cpu usage on HD movies once GPU acceleration is checked under inputs and codecs. My card is Intel HD3000 on my ASUS K53E i5 laptop.

---

### Post by drewdin on 2012-12-11
@[Linuxisfast]("http://ubuntuforums.org/member.php?u=1406702") I am doing a fresh install of 12.04, I would love to use my HD3000 videocard. All you did was install the package below? Thanks

libva-intel-vaapi driver

---

### Post by nickrout on 2012-12-11
> **drewdin said:**
> @[Linuxisfast]("http://ubuntuforums.org/member.php?u=1406702") I am doing a fresh install of 12.04, I would love to use my HD3000 videocard. All you did was install the package below? Thanks

libva-intel-vaapi driverYou will aloso need to set vaapi in your playback profile.

---

### Post by topcat5 on 2012-12-11
If you have room in your case, as noted above a GT 430 will work flawlessly and do audio over HDMI too.   Since they are being replaced by the GT 630 you should be able to find one for a low price.

---


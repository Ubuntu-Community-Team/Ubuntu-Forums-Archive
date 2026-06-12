---
title: "weird lines, font corrupted both in unity and gnome-shell"
date: 2012-04-28
forum: Multimedia Software
---

### Post by mattocompleto on 2012-04-28
I have a laptop (Samsung P200) with an ATI X1250, the chipset should be the R600 chipset with installed Ubuntu 12.04LTS.

As you can see, there are some weird lines in Unity and
Using Unity I can see some weird lines
[IMG]http://i46.tinypic.com/2ur55yp.png[/IMG]
[IMG]http://i49.tinypic.com/10hr30y.png[/IMG]
and in Gnome-Shell some font corruptions appear.
[IMG]http://img827.imageshack.us/img827/8899/gnome3.jpg[/IMG]

With the old version of Ubuntu with Gnome 2 there was any problem.

Somebody know this bug and how to solve it?

```

$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 1250 [1002:7942]

```

```

$ glxinfo 
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_INTEL_swap_event
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS600
OpenGL version string: 2.1 Mesa 8.0.2
OpenGL shading language version string: 1.20
OpenGL extensions:

```

---

### Post by doctor_juta on 2012-04-29
Have such problem too. Tested on Samsung R20 Plus (Ati Radeon X1251) under Ubuntu 11.10 and Ubuntu 12.04.

---

### Post by loe on 2012-04-29
I got a similar problem on my Thinkpad Z61m with an ATI X1400. In Unity, Gnome-Shell, Xfce and LXDE I get corrupt rendered fonts... Sometimes also some wired lines... 

When press "print" to make a screenshot everything gets redrawn and the corruption vansishes... :confused:

---

### Post by peculiar penguin on 2012-05-03
Could be related but I'm not sure that's the exact same issue, OP's (and my) problem shows up fine in screenshots.

It isn't new either, looking at Launchpad [it has been around since Oneiric at least]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/910624"), and it still occurs even when using the xorg-edgers PPA :(

---

### Post by davejrice on 2012-05-11
Hi peeps,

Just got hold of a Dell XT tablet PC. It also has the same x1250 gfx card and experiences the exact same problem.

I tried the xorg-edgers and it rendered the system unservicable - X failed to start.

hope we can get a solution to this - this little tablet laptop is very nice :)

cheers

DJ

---

### Post by peculiar penguin on 2012-05-18
welp

---

### Post by peculiar penguin on 2012-05-18
FWIW, I've jumped ship to Xubuntu, which seems to work fine for the few graphical bells and whistles I want from Compiz (Scale, Expo, Ring switcher).

---

### Post by metmayhem on 2012-05-22
I too have an X1250 and have the same exact problem. Has anyone found a solution to this?

---

### Post by Eestlane on 2012-06-18
Everybody having this problem click on "This bug affects me" link in [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/910624]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/910624")

I hate this bug as well!

Do you also have text corruption in some games, e.g Extreme TuxRacer?

---

### Post by peculiar penguin on 2012-06-25
[#751828   ]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/751828") is now the bug to watch/subscribe to/make noise about.

---

### Post by mack_guy911 on 2012-06-25
here i guess same bug 

but strange drivers are intel not Nvidia or ATI

[http://www.wilderssecurity.com/showthread.php?p=2077317](http://www.wilderssecurity.com/showthread.php?p=2077317)

---


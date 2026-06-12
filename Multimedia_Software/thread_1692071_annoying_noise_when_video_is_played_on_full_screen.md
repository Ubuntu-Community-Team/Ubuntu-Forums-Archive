---
title: "annoying noise when video is played on full screen mood"
date: 2011-02-20
forum: Multimedia Software
---

### Post by rez_noob on 2011-02-20
Hi, recently i installed ubuntu (gnome) 10.10. i'm lovin it but only thing is  bugging me is this annoying noise whenever i try to see a video on web or using vlc. i m using dell inspiron 6400. IT has VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400  My glxinfo outcome is : 

[HTML]name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV515
OpenGL version string: 2.1 Mesa 7.11-devel
OpenGL shading language version string: 1.20[/HTML]

Kernel driver in use: radeon
	Kernel modules: radeon


and my sound driver details Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
and also using usb head ph Microsoft LifeChat LX-3000. alsa information are here [http://www.alsa-project.org/db/?f=e1bd1e728957f36416d49d512ecaa2807689f35c](http://www.alsa-project.org/db/?f=e1bd1e728957f36416d49d512ecaa2807689f35c) 

now my main problem is whenever i change my visual settings from none to extra , i start getting noise on my usb headphone or even on my speakers especially if i play a video on full screen mode it become worse .. it starts constantly makeing buzzing noise. sometimes even when i minimize or maximize or scroll up down a window... if i put the visual effects in normal mode i still get the noise on video playing full-screen mood but this is time bit low and on none mode i get the noise too but very low... so i m assuming there must be some problem with my vga card which is causing this chaos. unfortunately there is no driver for my graphics card dat ati supports on ubuntu, so i used gallium 3d project using this ppa [https://launchpad.net/~xorg-edgers/+archive/radeon](https://launchpad.net/~xorg-edgers/+archive/radeon) .. graphics works fine now but this nosie is killing me .. 

can some1 please guide me what should it do to prevent it .. i searched a lot about this problem and even reinstalled ubuntu 2 times and even with the default graphics driver that came with new installation i had that buzzing noise... please help me n please pardon my poor English.. thanx

---

### Post by tjones00 on 2011-02-21
To me it sounds like a low power issue with your audio hardware.

-if you allow the gpu to consume more power your audio gets all borked.

Does this happen with the laptop is plugged into the ac adapter as well? Does the effect seem worse when the laptop is running strictly from battery?

I've read about odd screechy noise being a low power issue before. Unfortunately I have no experience correcting such an issue. So I can only give you a hint as to what it might be.

If memory serves me correctly I think it had something to do with pulseaudio forcing low power mode on the audio hardware. But I'm probably totally incorrect about this.

---

### Post by rez_noob on 2011-02-21
tjones00 thanx for the reply mate .. mate my laptops battery is dead soo i alwaz run it on power... but maybe u r right its happening because of the pulseaudio forcing low power mode cause every time i switch to extra or normal settings on appearance mode, my screen goes more bright with all the compiz effects working but then the sounds starts to cracking during the full screen video mode .. 

if could tell me how u fixed ur issue, i will try to see if it works .. thanks again

---

### Post by tjones00 on 2011-02-22
Sorry I've never had this issue I was just trying to give you a heads up as to what might be behind it.

---

### Post by rez_noob on 2011-02-22
its allright mate ...

is there anyone to help me here plzzz.............

---

### Post by rez_noob on 2011-02-23
no1 here to help me ???  :(

---

### Post by 11Aether11 on 2011-05-02
I have the same laptop (Dell E1505) and have experienced the same problem when watching full-screen video on the web (Youtube, Hulu). The sound starts cracking only in full-screen :/

Did you manage to solve this? It's mildly annoying and detracts from enjoying the whole experience :popcorn:

---


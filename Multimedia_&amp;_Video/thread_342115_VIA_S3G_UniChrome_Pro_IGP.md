---
title: "VIA S3G UniChrome Pro IGP"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by maksym on 2007-01-19
I know that this video card has been much discussed in the forums but I still cannot answer some basic questions. If the are clear answers - please direct me. I have lost two days now googling and installing/uninstalling ....

I have an Acer Aspire 1360 laptop (was bought not as a gaming machine obviously:)  ). The manual says it has integrated  "VIA S3G UniChrome Pro IGP" adapter.

I have no idea which modification of that adapter I have. Via web site lists a number of them under the above mentioned marketing name. glxinfo says it is **K8M800**:
```
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20060710
```

Now, 2D graphics works ok - meaning I can see desktop, it does not freeze, etc ;) However, 3D games, even "pouetChess" do not work. Moreover as soon as I start them my laptop freezes and refuses to talk to me. Completely. Only hard reboot helps.

What I did so far was trying out several things mentioned on ubuntu forums e.g
[http://www.ubuntuforums.org/showthread.php?t=115957]("http://www.ubuntuforums.org/showthread.php?t=115957")
(although for older ubuntu releases) - did not help - as well as trying to install the linux drivers from via website for K8M800 - got errors... 
Must admit that I do not alway understand what I am doing since relatively new to linux.

When I run glxgears I get :
```
libGL warning: 3D driver claims to not support visual 0x46
```
but I see the gears and they are moving. BTW - how do I know what I should see in case everything is fine? :mrgreen: 

Would appreciate if someone could answer these:
1. How can I identify what graphic card I really have? Under VIA/S3G UniChrome Pro IGP [www.viaarena.com](www.viaarena.com) lists CN700, CX700, K8M800/K8N800, KN400 & KM400, PM800, CN400, VN800, PN880.
2. Can I believe what glxinfo is telling me regarding the model of the graphic card (K8M800)?
3. what does "libGL warning: 3D driver claims to not support visual 0x46" mean? ](*,)  Maybe my IQ is well below average but 0x46 tells me nothing :-k 
4. If I see the 3D gears working (moving) after running glxgears - but 3D games do not work - does it mean that my 3D rendering is "half way" configured?
5. Has any one succeeded in running 3D games on VIA/S3G UniChrome Pro IGP adaper? On K8M800?
7. How do I test 3D, meaning is there a utility which would say " look, you have got this and this and you are missing this..."
6. Why does VIA/S3G UniChrome Pro IGP adaper suck in multiple operating systems including "user friendly" Win XP? :mrgreen: :mrgreen:  - Under my old windows World of Warcraft did work but only after a patch from Blizzard...

Please, do not suggest buying a new video card since it its a laptop and please do not say it is not for gaming since I was playing World of Warcraft OK in Win XP). Thank you.):P 

My xorg says:

```
Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

```

glxinfo:

```
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x46
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome (K8M800) 20060710
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x46 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

---

### Post by Tomy on 2007-01-19
>Would appreciate if someone could answer these:
>1. How can I identify what graphic card I really have? Under VIA/S3G >UniChrome Pro IGP [www.viaarena.com]("http://www.viaarena.com/") lists CN700, CX700, >K8M800/K8N800, KN400 & KM400, PM800, CN400, VN800, PN880.

you have properly identified it.

>2. Can I believe what glxinfo is telling me regarding the model of the >graphic card (K8M800)?
 
yes
 
>3. what does "libGL warning: 3D driver claims to not support visual 0x46" >mean? ](*,)  Maybe my IQ is well below average but 0x46 tells me nothing 

I get the same error message -- I believe it is harmless and can be ignored.

  >4. If I see the 3D gears working (moving) after running glxgears - but 3D >games do not work - does it mean that my 3D rendering is "half way" >configured?

no, 3d is working. There is a bug that was reported over a year ago that still has not been fixed. Many 3d games, and some 3d screensavers, freeze the computer solid. Nobody over at x.org seems to be maintaining the via 3d driver (dri). The via 2d driver is maintained by the good folks at openchrome.org. VIA does not cooperate with the open source community.

>5. Has any one succeeded in running 3D games on VIA/S3G UniChrome >Pro IGP adaper? On K8M800?

no, there is a bug. Some games may work.

>7. How do I test 3D, meaning is there a utility which would say " look, >you have got this and this and you are missing this..."
  
glxgears -printfps
glxinfo

you have already run these - your 3d is working.

>6. Why does VIA/S3G UniChrome Pro IGP adaper suck in multiple 
>operating systems including "user friendly" Win XP? :mrgreen: :mrgreen:  - Under my old >windows World of Warcraft did work but only after a patch from >Blizzard...

ask VIA. They provide an open source linux driver but only for some old versions of Red Hat and Suse. They do not help fix the bugs.

Join the crowd.
We are all frustrated.

---

### Post by maksym on 2007-01-20
Tomy, thanks a lot for such a comprehensive answer! Saved me much time of trying to fix "unfixible" :) .  I think switching to Ubuntu was worth just for the sake of community support. =D> .  
If this is a bug - well so be it. The laptop was bought when I was a student for the sole purpose of running matlab on it (now octave). It is a good one except for the lousy graphics. 
Cheers!

---

### Post by Bezmotivnik on 2007-01-29
After finally finding my v6.10 CD in a disused CD-ROM drive back in my studio, I loaded it up with my notebook and let fly.  Apparently, everything (except touchpad tap-tap function) is working in "Live" mode, including wireless and the Unichrome Pro video.

GLXGears shows 4110FPS+/- and I get what is apparently the same data as has been posted above, including the

   "libGL warning: 3D driver claims to not support visual 0x46"

...error.

So, considering I have zero interest in gaming, is this video arrangement going to work for all other routine tasks?  

As always, thanks for any help!:guitar:

---

### Post by maksym on 2007-01-29
> **Bezmotivnik said:**
> After finally finding my v6.10 CD in a disused CD-ROM drive back in my studio, I loaded it up with my notebook and let fly.  Apparently, everything (except touchpad tap-tap function) is working in "Live" mode, including wireless and the Unichrome Pro video.

GLXGears shows 4110FPS+/- and I get what is apparently the same data as has been posted above, including the

   "libGL warning: 3D driver claims to not support visual 0x46"

...error.

So, considering I have zero interest in gaming, is this video arrangement going to work for all other routine tasks?  

As always, thanks for any help!:guitar:

It does not effect normal work. as long as you dont play 3d games or do smth else 3d it is fine

---

### Post by khowe on 2007-02-03
The lock-ups are usually caused by shared IRQs.

put this in your /etc/X11/xorg.conf file under your Driver "via" line...

Option "DisableIRQ"
Option "EnableAGPDMA"

like so...

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"
        BusID           "PCI:1:0:0"
EndSection

---

### Post by maksym on 2007-02-03
> **khowe said:**
> The lock-ups are usually caused by shared IRQs.

put this in your /etc/X11/xorg.conf file under your Driver "via" line...

Option "DisableIRQ"
Option "EnableAGPDMA"

like so...

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"
        BusID           "PCI:1:0:0"
EndSection

Do you mean by "lock-ups" that the computer apeears to "freez" and does not respodn to any input when one tries 3d soft with unichrom?

---

### Post by khowe on 2007-02-03
Yes lock-up = freeze

---

### Post by Vox754 on 2007-02-13
If you find a fix to this let me know.

I have K8M800 for desktop PC.
It works okay, but yes, I also have problems with 3D screensavers. I don't even use screensavers anymore, just turn off the LCD monitor.
```

glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x46
2324 frames in 5.0 seconds = 464.683 FPS
2325 frames in 5.0 seconds = 464.852 FPS
2336 frames in 5.0 seconds = 467.150 FPS
2386 frames in 5.0 seconds = 477.119 FPS
2395 frames in 5.0 seconds = 477.417 FPS
2415 frames in 5.0 seconds = 479.181 FPS

```

After using this
```

Option "DisableIRQ"
Option "EnableAGPDMA"

```
I get better frame rate
```

glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x46
2918 frames in 5.0 seconds = 583.482 FPS
2976 frames in 5.0 seconds = 595.151 FPS
2974 frames in 5.0 seconds = 594.800 FPS
2977 frames in 5.0 seconds = 595.285 FPS
2977 frames in 5.0 seconds = 595.208 FPS

```

---

### Post by ..vitor.. on 2007-02-21
> **khowe said:**
> The lock-ups are usually caused by shared IRQs.

put this in your /etc/X11/xorg.conf file under your Driver "via" line...

Option "DisableIRQ"
Option "EnableAGPDMA"

like so...

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"
        BusID           "PCI:1:0:0"
EndSection

I have the same problem. Google Earth didn't work and freeze computer every time I launch it before. Now it's very beter.
But there is an other problem. There is a game called Cube ( [http://www.ubuntugames.org/cube](http://www.ubuntugames.org/cube) ) that can be run with onboard cards, but it doesn't works in my computer.
When I key in 'glxinfo' in command line it shows me:
"vitor@Ubuntu:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x46 (...)"

And when I try to run Cube I see:

"vitor@Ubuntu:~$ cube
libGL warning: 3D driver claims to not support visual 0x46
bin/linux_client: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory"

What is "visual 0x46"? How can I solve it?

In addition, some 3d screensaver doesn't works and freezes still...

Thanks

Vítor

---

### Post by sirbats on 2007-03-29
> **Tomy said:**
> >

  >4. If I see the 3D gears working (moving) after running glxgears - but 3D >games do not work - does it mean that my 3D rendering is "half way" >configured?

no, 3d is working. There is a bug that was reported over a year ago that still has not been fixed. Many 3d games, and some 3d screensavers, freeze the computer solid. Nobody over at x.org seems to be maintaining the via 3d driver (dri). The via 2d driver is maintained by the good folks at openchrome.org. VIA does not cooperate with the open source community.

Join the crowd.
We are all frustrated.

Hi Tomy,

I have Via P4M800 (Vga Chipset) UniChrome Pro IGP on IA-64 machine, but powered by edgy_x86 :=) : I tried openchrome driver, after installing driver from via : I got similar result. I back to openchrome driver. 3D is working by meaning : I can install LG3D desktop (Looking Glass Project) and confirm worked. But I have zero interest to game. 

I can install[ LG3D]("https://lg3d.dev.java.net") by down-grade the color depth from 24 to 16 in the /etc/X11/xorg.conf.

---

### Post by ronda on 2007-06-10
> **maksym said:**
> 
 I was playing World of Warcraft OK in Win XP). Thank you.):P 
[/CODE]

ok i play wow and i have this graphic card or watever, and WoW crashes on me half the time, mostly when i hearth (teleport) from one place/city to another. when this happens i cannot log back into the character that iwas playing when the crash happened, my computer will just crash again and agian every time i try.  Another problem i have is that the graphics for the ground are not rendered correctly. i have linked a couple of my screen shots to better explain wat i mean. 

[http://i204.photobucket.com/albums/bb244/ronda_88/WoWScrnShot_021507_095732.jpg](http://i204.photobucket.com/albums/bb244/ronda_88/WoWScrnShot_021507_095732.jpg)

[http://i204.photobucket.com/albums/bb244/ronda_88/WoWScrnShot_021507_095723.jpg](http://i204.photobucket.com/albums/bb244/ronda_88/WoWScrnShot_021507_095723.jpg)

[http://i204.photobucket.com/albums/bb244/ronda_88/WoWScrnShot_010207_021344.jpg](http://i204.photobucket.com/albums/bb244/ronda_88/WoWScrnShot_010207_021344.jpg)

any ideas on how to stop this from happening are much appreciated

---

### Post by Selector on 2007-07-06
I've red the most of the info here.Question: you mean that with this video card I can't play games like WoW,Counter Strike,Metal Gear Solid 2 Substance etc. .. .? :(

---

### Post by maksym on 2007-07-06
Exactly, this card is a pain to play these games even in windows, where you have the propriatory drivers. It is slow and graphics looks bad. Since the manufacture does not support linux fully - it is even worse in ubuntu. Not the ubunu probelm. If you want to play games but have this card - throw the laptop away and buy nvidia/ ati :(

> **Selector said:**
> I've red the most of the info here.Question: you mean that with this video card I can't play games like WoW,Counter Strike,Metal Gear Solid 2 Substance etc. .. .? :(

---

### Post by khowe on 2007-09-16
You can try irqpoll boot option.
this can be added to /boot/grub/menu.lst
add it after the quiet splash.

I have had the most success with ubuntu 6.10 edgy.
feisty and gutsy have caused lock-up, freeze for me when ever I run a 3d app.
I have an averatec 3715 laptop.

I found this in a bug report @ [https://bugs.launchpad.net/ubuntu/+s...via/+bug/43154]("https://bugs.launchpad.net/ubuntu/+s...via/+bug/43154")

I'm not sure if I got the same problem:
Everything worked fine until Feisty.
My card is a KM400 and since Feisty I get complete freezes (but the mouse cursor is still moveable) when i run ANY 3d related application. Even a simple glxinfo freezes the system.
I don't find any error messages in the logs and i can start the X-Server with via specified in the xorg.conf but as soon as 3D is required the fun is over.

I solved this problem for me by downgrading libgl1-mesa-glx and libgl1-mesa-dri from 6.5.2-3ubuntu7 (Feisty) to 6.5.1~20060817-0ubuntu3 (Edgy).

My card has never worked by default, even if Ubuntu recognizes it in the installation process (which it does since Edgy, I guess).
Additional options which I have always needed to get it working are:
Option "VBEModes" "true"
Option "DisableIRQ"
Option "EnableAGPDMA"

same info also @ [https://bugs.launchpad.net/ubuntu/+s...sa/+bug/118163]("https://bugs.launchpad.net/ubuntu/+s...sa/+bug/118163")

---

### Post by Vox754 on 2008-01-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/43154](https://bugs.launchpad.net/bugs/43154) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **maksym said:**
> Exactly, this card is a pain to play these games even in windows, where you have the propriatory drivers. It is slow and graphics looks bad. Since the manufacture does not support linux fully - it is even worse in ubuntu. Not the ubunu probelm. If you want to play games but have this card - throw the laptop away and buy nvidia/ ati :(

Yes, you are right. But don't top-post.

A: Top-posting.
Q: What is the most annoying thing on the internet?

Sign the petition.
[http://www.PetitionOnline.com/vialinux/](http://www.PetitionOnline.com/vialinux/)

---

### Post by zakaria.cse on 2008-07-14
At last my screen resolution is working perfectly. Here is what I did:
[LIST=1]
[*]Visited "VIA Linux Portal" site: [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
[*]Chose OS as: Ubuntu & Platform as: CN700+VT8237S/VT8237R Plus
[*]Downloaded GFX driver file, extracted it and installed it from terminal.
[/LIST]

Be sure to choose correct platform type for your via graphics device. You will find hardware information by typing following command into terminal:
```
sudo lshw
```

Then search for your correct pci product information, those are listed as "Platform" on "VIA Linux Portal" site.


:guitar:

Thanks a lot!

---


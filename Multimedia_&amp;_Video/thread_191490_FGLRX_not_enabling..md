---
title: "FGLRX not enabling."
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by Echo35 on 2006-06-07
I noticed that my 3D applications were running abnormally slowly. When I investigated into the cause, I realized that my computer was using the Mesa driver, which I understand won't interface with my hardware (ATI Raedon 9200 SE) for 3D accelleration. I downloaded and installed the FGLRX drivers and followed all the how to's, but no matter what I do, the FGLRX driver will not enable. The Mesa 3D driver is always there and will not switch over to the FGLRX one, which would make my 3D applications work. Can anyone help me with this?

---

### Post by JohnDoeJr on 2006-06-07
Same problem with a 9200 radeon mobilty on a Acer notebook.. I also tried the ATI drivers but there is no accelleration except mesa.

---

### Post by matc on 2006-06-07
Same problem here with Radeon 9000 on my desktop system.

---

### Post by Echo35 on 2006-06-08
If you enable the FGLRX driver, there is 3D accelleration. I have done it before. It worked fine on my Breezy Badger install, but I did a fresh install to Dapper Drake, and now I have to figure out how I did it...

---

### Post by frank_b on 2006-06-09
Same thing here.


I have a Radeon 9250 SE card and if I follow the instructions in [https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI), I can't get fglrx enabled also.


The instructions are not clear, when it reaches the

> Under Section "Screen" The Identifier line needs to be changed to:

     Identifier "aticonfig-Screen[0]"

since I get two "Screen" sections after the "aticonfig" commands and one of them already has that in the "Identifier" section.


If I assume the change is already done and leave them as they are, I get a list of error messages with the "fglrxinfo" command:
> 
[fglrx] API ERROR: could not register entrypoint for "*this and that*"

If I assume the section the tutorial talks about is the one left unchanged and change that one, the result beeing having now the two "Screen" sections with "Identifier "aticonfig-Screen[0]"", I get the same result with the "fglrxinfo" command I got before doing anything:

> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.


With 5.10 I could get it enabled following the tutorial...


If I can solve my problem I'll post the solution here.

Please do the same.

---

### Post by Turin Turambar on 2006-06-09
Apparently this is a bug, ATI driver does not work good with Xorg 7.0. At least, that's what I've heard. I have the same problems with Radeon 9000.

As I said, this is a flop for Ubuntu team to have these kind of bugs still around...

---

### Post by Ivhassel on 2006-06-09
[QUOTE=Turin Turambar]Apparently this is a bug, ATI driver does not work good with Xorg 7.0. At least, that's what I've heard. I have the same problems with Radeon 9000.

As I said, this is a flop for Ubuntu team to have these kind of bugs still around...[/QUOTE]

Try this howto, solved my problems, along with many others'. We happen to have the same ATI card too ...

[http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26)

---

### Post by frank_b on 2006-06-09
Installing older versions of the "xorg-driver-fglrx" package and "recompile the kernel module after each kernel update" like it's described in [http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26) sounds like a potential mess for someone who doesn't understand much of the procedures in question. Sounds like it might mess with the updates...

I guess I'll patiently wait for updates in the "BinaryDriverHowto/ATI".

I've already send an e-mail warning the last person who edited the tutorial.

---

### Post by Ivhassel on 2006-06-10
[QUOTE=frank_b]Installing older versions of the "xorg-driver-fglrx" package and "recompile the kernel module after each kernel update" like it's described in [http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26) sounds like a potential mess for someone who doesn't understand much of the procedures in question. [/QUOTE]
Agreed, it means if they just click "apply updates" then the new ATI driver gets installed, and they're back where they left off. Possibly without even realizing they installed the latest drivers.

But I haven't found a better way to fix my issues with the ATI driver & my R250 card. If you happen to solve it in a neater way, please do. 

Then again, I'm the person that checks out every package he installs, before clicking "apply upgrades" :)

[QUOTE=frank_b]Sounds like it might mess with the updates...[/QUOTE]

Yeap, but you can find all the info you need, to fix that here:
```

in a terminal: man apt_preferences
in konqueror: man:apt_preferences

```

I blacklisted the ATI driver that fucks up my install (the one from fglrx), and assigned a priority of 1001 to the previous one. That's going to stay like that until I see a notice that the next ATI driver works with my card.

---

### Post by eRoot on 2006-06-10
[QUOTE=frank_b]Same thing here.


I have a Radeon 9250 SE card and if I follow the instructions in [https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI), I can't get fglrx enabled also.


The instructions are not clear, when it reaches the



since I get two "Screen" sections after the "aticonfig" commands and one of them already has that in the "Identifier" section.


If I assume the change is already done and leave them as they are, I get a list of error messages with the "fglrxinfo" command:


If I assume the section the tutorial talks about is the one left unchanged and change that one, the result beeing having now the two "Screen" sections with "Identifier "aticonfig-Screen[0]"", I get the same result with the "fglrxinfo" command I got before doing anything:




With 5.10 I could get it enabled following the tutorial...


If I can solve my problem I'll post the solution here.

Please do the same.[/QUOTE]
Sorry, but the quote function doesn't seem to get codeblocks.
Anyway, you say that after you install the fglrx driver, you get the "API errors". This can be easily solved by replacing the libGL.so.1.2 file in /usr/lib by an older version.
I have included the (older) file in an attachment, so all you have to do is install fglrx again, just like you did before, and then replace the file.

---

### Post by KiLLeR_WoMBaT on 2006-06-10
I got no errors...but still no 3D.  Here is the output of fglrxinfo:

daniel@ubuntu-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

daniel@ubuntu-laptop:~$

Any suggestions?

---

### Post by Ivhassel on 2006-06-10
Killer_Wombat,
Without any info, no one can help...


Please post the following info:

[LIST]
[*]Output of
```
lspci | grep ATI
```
[*]Output of
```
fglrxinfo
```
[*]Output of
```
glxinfo
```
[*]Your /etc/X11/xorg.conf
[*]What error messages do you get? Possibly this: [fglrx] API ERROR: could not register entrypoint for *$API*
[/LIST]

---

### Post by KiLLeR_WoMBaT on 2006-06-10
Sorry.  Here is some info:

daniel@ubuntu-laptop:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

daniel@ubuntu-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

daniel@ubuntu-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

I hope that all helps.  There is one weird indication when trying to use fglrx or ATI drivers by selecting them with aticonfig or manually editing the /etc/X11/xorg.conf file.  Upon boot the login screen will give TWO drum sounds.  When this happens I know the computer is going to hang after login.  It just sits there with the brown background and the mouse cursor.  After changing it back to use VESA then I get the single drum sound at the login screen and everything is fine.

Here is the xorg.conf:

---

### Post by Ivhassel on 2006-06-10
[QUOTE=KiLLeR_WoMBaT]Sorry.  Here is some info:

daniel@ubuntu-laptop:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10][/QUOTE]

A card with that chipset (R350) works with the fglrx from the repos. 
Try to reinstall your fglrx drivers with synaptic. ;)

---

### Post by Perfex on 2006-06-10
[QUOTE=Ivhassel]A card with that chipset (R350) works with the fglrx from the repos. 
Try to reinstall your fglrx drivers with synaptic. ;)[/QUOTE]

wierd in breezy I could not get it to work with my 9700 pro, but in dapper I had no problems what so ever getting it enabled.

---

### Post by KiLLeR_WoMBaT on 2006-06-10
[QUOTE=Ivhassel]A card with that chipset (R350) works with the fglrx from the repos. 
Try to reinstall your fglrx drivers with synaptic. ;)[/QUOTE]

This card worked fine with Breezy but I can't for the life of me get it to work with Dapper.  I did the update from breezy three times.  I do not have the cd to do a clean install.  And I have reinstalled with synaptic half a dozen times.  Still no 3D just Mesa.

---

### Post by frank_b on 2006-06-11
Thanks for your help lvhassel, but I don't like the idea of reconfiguring a lot of things in my computer, just to have to reconfigure them all back once the bug is solved.

Thanks for the file eRooot, but from what I read, this is either a bug with the fglrx driver or xorg.

I have other distros I wanna try out, so I guess I'll wait for some bug fix or something while I try them.

---

### Post by Turin Turambar on 2006-06-11
Damn it. My patience is running over....

---

### Post by Andenium on 2006-06-13
Question is "How do i replace the libGL.so.1.2 file in /usr/lib by an older version??"

---

### Post by Ivhassel on 2006-06-13
[QUOTE=Andenium]Question is "How do i replace the libGL.so.1.2 file in /usr/lib by an older version??"[/QUOTE]

```

sudo cp /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1.2.backup ## always backup
sudo cp /path/to/old//usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1.2

```

then restart your x-server.

---


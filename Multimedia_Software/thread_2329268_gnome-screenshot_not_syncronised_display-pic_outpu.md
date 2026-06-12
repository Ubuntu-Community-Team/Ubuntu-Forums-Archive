---
title: "gnome-screenshot not syncronised display-pic output"
date: 2016-06-29
forum: Multimedia Software
---

### Post by banceu_sergiu_ione on 2016-06-29
My problem is that I get this output when I do screen-shot

[ATTACH=CONFIG]269856[/ATTACH]

I had install Kazam to see if I get same error while screen-shot, and yes. 

But, as soon I had configured Kazam at 60fps and had run a screen recorder session, if I screen-shoot after it all work good, and the pic. output is as have to be.

[ATTACH=CONFIG]269858[/ATTACH]

If i reboot it return to have the same as 1st SS.

I had thought that I may have a bad display frame synchronization, but I don't know what to check and to modify. Its stand that its all good if I 1st run a screen record.

Here are same more specs about my pc.
Toshiba L50D-C-18X AMD A10 8700P Carrizo
> 
fex@fex:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

fex@fex:~$ uname -a
Linux fex 4.4.0-28-generic #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

fex@fex:~$ glxinfo | grep 'version'
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
    Max core profile version: 4.3
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.1
OpenGL core profile version string: 4.3 (Core Profile) Mesa 12.1.0-devel - padoka PPA (git-6b0ac95)
OpenGL core profile shading language version string: 4.30
OpenGL version string: 3.0 Mesa 12.1.0-devel - padoka PPA (git-6b0ac95)
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 12.1.0-devel - padoka PPA (git-6b0ac95)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10

fex@fex:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 16384 x 16384
eDP connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768      60.00*+
   1280x720      59.86  
   1152x768      59.78  
   1024x768      59.92  
   800x600       59.86  
   848x480       59.66  
   720x480       59.71  
   640x480       59.38  
HDMI-A-0 disconnected (normal left inverted right x axis y axis)
HDMI-A-1 disconnected (normal left inverted right x axis y axis)

Let me know if (what) more info needed.
Thank You.

---

### Post by banceu_sergiu_ione on 2016-07-04
dropping padoka PPA and get on default mesa make it solve

---


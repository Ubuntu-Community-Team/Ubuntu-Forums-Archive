---
title: "How to enable openGL?"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by Castigate on 2006-11-19
Hi, I wanted to know if someone could help me out. I had my graphic card working fine when I first installed ubuntu because the screensaver would work in openGL mode. Then after I changed to Kubuntu I realized my screensaver wouldn't work on any of the (GL) settings. Also Google Earth doesn't run properly. I have a crappy video card but it's all I have for now. It's a RIVA TNT2 AGP 32MB. Im also Using Althlon 1700+ with 768MB of SDRAM. Thank's in advance.

---

### Post by whatever on 2006-11-19
install the nvidia legacy drivers

---

### Post by Castigate on 2006-11-19
After installing the nvidia legacy drivers the computer only boots to command line.  What should I do now](*,)

---

### Post by Castigate on 2006-11-19
I got my system back up and the nvidia legacy drivers are installed.  I'm still having the same problem with openGL.  Can anybody help?:confused:

---

### Post by ashmew2 on 2007-01-03
HI , i myself have a NVIDIA Geforce 4000 wit 64 MB V-RAM , im trying to run Cedega on ubuntu but when i run tests , it says that the OpenGL test failed.I have already installed Nvidia Drivers which prevented my comp from booting twice into graphical mode and then it got fixed by itself..  I used command : sudo aptitude install nvidia-glx 
Now how do i enable OpenGL... ? :P
THanks

---

### Post by tseliot on 2007-01-03
> **ashmew2 said:**
> HI , i myself have a NVIDIA Geforce 4000 wit 64 MB V-RAM , im trying to run Cedega on ubuntu but when i run tests , it says that the OpenGL test failed.I have already installed Nvidia Drivers which prevented my comp from booting twice into graphical mode and then it got fixed by itself..  I used command : sudo aptitude install nvidia-glx 
Now how do i enable OpenGL... ? :P
THanks

post the output of this command:
```
glxinfo | grep direct
```

---

### Post by ashmew2 on 2007-01-03
when i run command :  glxinfo | grep direct
I get :
ashish@The-Ub3r-L33t:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by tseliot on 2007-01-03
Direct rendering is disabled.

Try envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ashmew2 on 2007-01-04
Thanks tseliot! For the awesome script Envy :) It installed my NVIDIA Driver as easily as eating candy :P But the problem is like not fully solved now lol. When i again run all the tests , it Passes on OpenGL but it fails on 3D Acceleration. Now what do i do ? :( 
when i run command glxinfo , it outputs :
Direct Rendering : Yes

Any ideas Any1 ? Thanks

---

### Post by wcampbell on 2007-04-07
I have the exact same problem, but I'm using Feisty.... Envy does not appear to be available for feisty.... the driver is listed in "restricted drivers manager" but says "needs computer restart" and stays that way after reboot.  result from glxinfo | grep direct is the same as above.

any help would be greatly appreciated.

~Warren

---

### Post by Ophie on 2007-04-13
ubuntu now will only boot to command line after installing envy and the nvidia drivers. Can anyone tell what exactly do I have to do in order to get it back the way it was also with OpenGL enabled?

---

### Post by d98rolb on 2007-04-22
I'm newbie myself in Ubuntu, but I think you have to use a old backup copy of xorg.conf that contains infor about graphic drivers etc.

So boot ubuntu in recovery mode.
type 

[FONT="Fixedsys"]cd /etc/X11
ls -l xorg.*
[/FONT]

This will show a list of files
xorg.conf is the current config.
Note the filename of the file slighty more older than xorg.conf, for example xorg.conf_backup
To use an old copy write

[FONT="Fixedsys"]sudo cp xorg.conf_backup xorg.conf

sudo shutdown now -r[/FONT]

---

### Post by manshri on 2007-08-23
Hi all,

 I am also on feisty and had the same problems. Here's how i solved them.


Case : I have a compaq presario f500 with nvidia geforce go 6100. achitecture is x86_64/amd64 

I got nvidia_glx_new package from apt.
used nvidia-xconfig to build an initial xorg.conf.
```

 nvidia-xconfig
nvidia-xconfig -composite;nvidia-allow-glx-with-composite
nvidia-xconfig -render-accel;nvidia-xconfig -add-argb-glx-visuals

```

These are for enabling basic options for direct rendering and 3D acceleration.

now, 

check 
```

ls -l /usr/lib/libGL.so.*

```
you would have some file similar to libGL.so.1.0.9755 in the structure but libGL.so.1 would be pointing to libGL.so.1.2 or some such file
do
```

rm /usr/lib/libGL.so.1
ln -s /usr/lib/libGL.so.1.0.9755 /usr/lib/libGL.so.1

```

repeat the same thing in /usr/lib32 to get cedega working. This is necessary as cedega uses 32 bit libraries.

now glxinfo should give you direct redering: yes 
and cedega should pass the video tests.

Hope it helps

---


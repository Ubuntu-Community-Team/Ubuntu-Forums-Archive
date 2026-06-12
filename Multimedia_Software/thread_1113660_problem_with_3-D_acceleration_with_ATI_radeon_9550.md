---
title: "problem with 3-D acceleration with ATI radeon 9550 (256 MB)"
date: 2009-04-01
forum: Multimedia Software
---

### Post by 10/4 on 2009-04-01
hi. i'm kind of new to linux. i tried to install driver for ATI radeon 9550 from the ATI web-site. does anyone know how to properly enable 3-d acceleration? also, when i try to go into catalyst control, i get an error telling me there are no ati drivers installed. also, direct rendering is disabled. the last time around i screwed things up so bad i had to re-install the whole OS. this is a clean install, and the ATI drivers were the first thing i installed. help and expertise would be greatly appreciated. thanks, 10//4:guitar:

---

### Post by wolfen69 on 2009-04-01
install the drivers from system>administration>hardware drivers.

---

### Post by ziadnahas on 2009-08-05
Can some one please help. I have a problem with my Ati Radeon 9550 card. I'm trying to run Mythtv on Ubuntu 9.04. I have figured out that the graphics card requires certain drivers to accomadate 3d functinality. 
 
I understand that Ubuntu has a how to install for ATI's. However, it requires to go to 'Hardware Drivers' and enable drivers, before entering a few comands in the terminal. Unfortunatly, when i go to Hardware drivers, there are no drivers and hence can not enable this function before proceeding to the comands in terminal.
 
I have looked at other archived forums on Ubuntu, but were not helpful. These forms were old and the required files were not availbe anymore. The other problem is i'm very new to Ubuntu and the linux comands. So really just relying on copy and pasting comands.
 
Your assistance would be much appreciated...

---

### Post by Mikeplus14/27 on 2009-08-22
> **ziadnahas said:**
> Can some one please help. I have a problem with my Ati Radeon 9550 card. I'm trying to run Mythtv on Ubuntu 9.04. I have figured out that the graphics card requires certain drivers to accomadate 3d functinality. 
 
I understand that Ubuntu has a how to install for ATI's. However, it requires to go to 'Hardware Drivers' and enable drivers, before entering a few comands in the terminal. Unfortunatly, when i go to Hardware drivers, there are no drivers and hence can not enable this function before proceeding to the comands in terminal.
 
I have looked at other archived forums on Ubuntu, but were not helpful. These forms were old and the required files were not availbe anymore. The other problem is i'm very new to Ubuntu and the linux comands. So really just relying on copy and pasting comands.
 
Your assistance would be much appreciated...

I'm in the same situation as ziadnahas - running Kubuntu 9.04 instead though.

While system >> hardware drivers opens, says it detects hardware and searches for drivers nothing appears at all on the lists - and I know that the graphics card itself supports graphics acceleration.

'glxinfo | grep render' returns with: 

"direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX/SSE2 TCL"

But even though it says that direct rendering is enabled things run waaaaaaaaay slower than they do in Windows (Blender and Wings 3d for example) and don't support more 'advanced' modes as they did in Windows (like GLSL materials in Blender and the advanced shaders in Wings 3d).

Any help would be greatly appreciated, been searching around for solutions for this for a while now. :popcorn:

Sorry to bump a 2 week old post (hope that doesn't count as 'old' ;) ).

---

### Post by steefjeqv on 2009-08-22
Hi,

Don't use the ATI closed source driver (fglrx). Your graphics card isn't supported anymore.

Have a look at this thread (post nr. 32) :

[http://ubuntuforums.org/showthread.php?t=1174943&page=4]("http://ubuntuforums.org/showthread.php?t=1174943&page=4")

Before you use the xorg on the edge ppa, first make sure fglrx (ATI driver) is completely removed (terminal) :

sudo dpkg --purge fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx

Greetings,
Steven

---


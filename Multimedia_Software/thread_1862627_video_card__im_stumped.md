---
title: "video card ? im stumped"
date: 2011-10-16
forum: Multimedia Software
---

### Post by rrembold on 2011-10-16
ok everyone im very new to this ubuntu and i need some help please. I have just installed ubuntu 11.04 on an old dell desktop that has a intel corp 82845g/gl video card and i cant seem to figure out how to enable the 3d cube, sphere ect.. and i would really like to but i dont know where to start and or if its even possible any and all help would be great. It only lets me log into ubuntu classic, if i try ubuntu the screen doesnt act right. also i didnt install the third party apps when i installed ubuntu should i have installed these?

---

### Post by BicyclerBoy on 2011-10-17
Ubuntu should be using the intel driver (open source) that supports 815 845 915 etc. It may not be enabled.

Don't expect to much from old intel graphics..but the 945 1st gen atom graphics runs Unity 3d very well.

To check the opengl driver:

glxinfo | grep OpenGL
cat /var/log/Xorg.0.log | grep DRI

---

### Post by rrembold on 2011-10-17
ok im sorry but how do i check the opengl driver:

glxinfo | grep OpenGL
cat /var/log/Xorg.0.log | grep DRI ? 
 
and where could i get 945 1st gen atom graphics ?

---

### Post by BicyclerBoy on 2011-10-17
You need to open a terminal window (<ctrl>+<alt>+<T>) on your GUI desktop (X server screen).
Then type in the commands...
Copy output (or redirect into text file).
Paste into forum post or attach text file.

The comment about netbook atom 945 was just to indicate that Unity 3d runs on some lower power graphics..so don't give up hope..

---

### Post by rrembold on 2011-10-20
ok this is what i got dont know what it means or if i did it right though


robert@robert-Dell-DE051:~$ glxinfo | grep OpenGL
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
robert@robert-Dell-DE051:~$ sudo apt-get install mesa-utils
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 237 not upgraded.
Need to get 27.6 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe mesa-utils i386 8.0.1+git20110129+d8f7d6b-0ubuntu2 [27.6 kB]
Fetched 27.6 kB in 0s (29.9 kB/s)     
Selecting previously deselected package mesa-utils.
(Reading database ... 132646 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
robert@robert-Dell-DE051:~$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.10.2
OpenGL extensions:
robert@robert-Dell-DE051:~$ cat /var/log/Xorg.0.log | grep DRI
[    18.529] (II) Loading extension XFree86-DRI
[    18.530] (II) Loading extension DRI2
[    18.840] (II) intel(0): [DRI2] Setup complete
[    18.840] (II) intel(0): [DRI2]   DRI driver: i915
[    18.896] (II) intel(0): direct rendering: DRI2 Enabled
[    18.914] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    18.941] (II) GLX: Initialized DRI2 GL provider for screen 0
robert@robert-Dell-DE051:~$

---

### Post by BicyclerBoy on 2011-10-20
That all looks good..

Run this from terminal:

/usr/lib/nux/unity_support_test -p 

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)


Can you trying logging in to Unity 3d again ?

---

### Post by rrembold on 2011-10-21
also i tried this on my other old dell and this is what i got with this one 

rob@rob-OptiPlex-GX260:~$ glxinfo | grep OpenGL
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
rob@rob-OptiPlex-GX260:~$ sudo apt-get install mesa-utils
[sudo] password for rob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.6 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe mesa-utils i386 8.0.1+git20110129+d8f7d6b-0ubuntu2 [27.6 kB]
Fetched 27.6 kB in 1s (24.3 kB/s)
Selecting previously deselected package mesa-utils.
(Reading database ... 157598 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
rob@rob-OptiPlex-GX260:~$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
OpenGL extensions:
rob@rob-OptiPlex-GX260:~$ cat /var/log/Xorg.0.log | grep DRI
[    18.402] (II) Loading extension XFree86-DRI
[    18.402] (II) Loading extension DRI2
[    18.546] (II) AIGLX: Screen 0 is not DRI2 capable
[    18.546] (II) AIGLX: Screen 0 is not DRI capable
[    18.546] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    18.571] (II) GLX: Initialized DRISWRAST GL provider for screen 0
rob@rob-OptiPlex-GX260:~$ 

does this one look good also?

ill

---

### Post by BicyclerBoy on 2011-10-21
No good
software rasteriser & no DRI..

That applies no specific video driver just vesa ?
lspci | grep VGA

About the compiz cube & unity..
It must be possible (internet evidence) but it is not easy.
Expect config crashes/console logins/ unity resets etc.

11.04 Unity is/was not ready for full compiz plugins only a preset/subset.

You would be better to use 10.10 or some other desktop that does not use unity.

---

### Post by rrembold on 2011-10-23
ok well i think i tried to log into unity but im not sure lol when i sign in when the comp starts my choices are recovery console, ubuntu, ubuntu classic, ubuntu classic (no effects), ubuntu safe mode, and usr defined session. i tried ubuntu (i guess thats unity 3d ?) but when i get to the desktop everything acts weird and when i go to click on an app or window it just keeps blinkg and disapears. Out of ubuntu , ubuntu classic and  ubuntu classic no effects, ubuntu classic is the only one that acts right. also when i ran that test this is what i got 

robert@robert-Dell-DE051:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  1.3 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no
robert@robert-Dell-DE051:~$

---

### Post by rrembold on 2011-10-23
also originaly i posted it had  intel corp 82845g/gl (dell GX260) but this is the comp that you said was no good and the one that you said was good has 82865g (dell DE051). sorry for the wrong info

---

### Post by BicyclerBoy on 2011-10-23
That's okay I can see the video h/w in the OpenGL stuff & the computer name in the shell info..

I think Unity takes a conservative approach to supported video cards..
I'm sure it can be over-written to force your graphics.

**But **the line about GL fragment program = NO (pixel shader) may be the show stopper..
I doubt any driver update can fix..must be h/w.

I think this means you **can only use Unity 2d **(package unity-2d)

Do you have a PCIexpress slot in any of these computers ?
A good half height PCIe card is only $40..(GT220,520 )

---


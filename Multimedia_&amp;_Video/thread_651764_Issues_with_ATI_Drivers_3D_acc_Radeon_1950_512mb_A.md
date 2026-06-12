---
title: "Issues with ATI Drivers 3D acc Radeon 1950 512mb AGP"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by Kleppemeister on 2007-12-27
I've been trying to get my PowerColor X1950 PRO 512MB AGP card to work properly with Ubuntu 7.10 for 5 weeks now(In the start I diden't quiet know what to do, so I did alot of reinstalling of the OS) I've followed countless amounts of guides. Found alot here on the forums, and alot diffrent by googleing. Everything from outdated guides to newly created guides. I've gotten the pleasure of learning alot about how things work, with trying and failing, and is really starting to enjoy the experience called Linux.

The issue I got is kinda hard to explain, but the end thing is, i cant really get it working. The display is showing everything correctly now days. But i really wanna get 3D acceleration enabled. I manged to do it once. Everything got kinda sluggish then, but it did work, the was witht the restriced drivers.. But when the next time i rebooted everything died out on me, and my screen went... all... I dont know what word i would us for it, but it looked like the refresh rate for the screen was of the charts. WHen i manged to check what the refresh rate was, it was at 60. And that should work. (and it do now, just not with 3D acc working)

Another thing when I follow another guide is that the screen just blacks out. And another guide just make the screen stuck at a really low res. And when i change it, its still stuck at the same ressolution.

But about 80% of the issues are related to(I would guess they are atleast) the restricked drivers, since its after i enable them, and reboot i get most issues.

So what I am wondering about is if anyone have any suggestions on how I might be abel to make this work. Im not going to give up on this. In the begining I was really hating Linux, but the more i read, and the more i started to learn, the more I loved the whole experience that is Linux.

I get this when i do fglrxinfo in terminal

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

And I've tyed the solution on the guide How to install ATI Driver on any stabel version of Ubuntu

Also i get this: 

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

when doing: LIBGL_DEBUG=verbose fglrxinfo

---

### Post by Kleppemeister on 2007-12-28
Been trying a few more times to get it working. But right now im stuck at 800x600 ressolution, and cant seem to get back to 1280x1024. Tryed to change a few files from diffrent guides ive read before. But this time Im stuck, and get seem to get back, I dont find any guides that helps me out, even if I have tryed them this time around. Not sure what I can try now. 

Is the only way to get back to reinstall Ubuntu this time? Have i tryed to much and maybe messed to many files up ?

---


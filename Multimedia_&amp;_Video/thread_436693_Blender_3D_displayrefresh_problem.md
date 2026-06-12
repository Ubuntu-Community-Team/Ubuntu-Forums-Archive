---
title: "Blender 3D display/refresh problem"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by KIAaze on 2007-05-08
I have installed Blender through synaptics package manager.
However, I am having some weird display problems as seen in this picture:
[IMG]http://img522.imageshack.us/my.php?image=blenderproblemoy5.png[/IMG]
[http://img522.imageshack.us/my.php?image=blenderproblemoy5.png](http://img522.imageshack.us/my.php?image=blenderproblemoy5.png)


Menus and 3D windows are incomplete. When I go over missing parts with the mouse, they get displayed, but it seems pretty unstable.
When I move around the scene, there's no refresh: everything gets drawn above the previous image.

Pressing the tab key to swith between edit and object mode refreshes the screen, but not always completely.

How can I solve this problem?
Other than the display, the program works. I was able to complete the smiley and heart creation tutorials and when saving the scene as jpeg, the image is fine.
But having appearing/disappearing menus and partially rendered 3D scenes is quite unpractical...
I have an ATI IGP 345M video card with 64MB shared memory.
3D games work well.

---

### Post by cryptic3481 on 2007-06-14
did anyone solve this problem. I as well had screen issues. tried other threads but I nothing as of yet worked. it's exactly how this person explained except i have a different vid card. thanks for any help if any.

---

### Post by KIAaze on 2007-06-16
Well, for the moment, you can also use [K3D]("http://www.k-3d.org/wiki/Main_Page") instead. (it's also in the repositories)
It even has built in animated tutorials, which I really liked. :)

But I still haven't solved the Blender problem. :(
I don't understand why it doesn't seem to work correctly under Ubuntu, since it's such a famous 3D software.

I can't figure out what kind of GUI they are using. It doesn't seem to be GTK or Qt.
I think I'll try finding their mailing-list and post the problem there.

I don't really do 3D work, but I wanted to try it out a little bit since I would like to try to use self-created 3D models in a game (altough I still have a lot to learn before that ^^).

---

### Post by cyberkoa on 2007-06-18
The latest blender update package only partially solve the window-mode , the window is still not viewable.

Screen refresh really problem because the desktop seems break the blender screen.

---

### Post by trellis on 2007-06-29
i ve got this problem too , i have a ATI Mobility Radeon 7500 .

---

### Post by KIAaze on 2007-07-01
I tested Blender on Windows with my PC and it works well.

I tried creating an account on the Blender site to report this as a bug, but I keep getting this after clicking on the link of the confirmation e-mail and trying to log in:
> Access denied

Credentials you entered do not correspond to valid account.

Strange...

edit:
Possible solutions: [http://blenderartists.org/forum/showthread.php?t=13255]("http://blenderartists.org/forum/showthread.php?t=13255")
Especially this:
> **3D-Penguin said:**
> Hi Blenderheads,

looks like the windoze ppl have better OpenGL Support for Blender.
What makes me worry is just that Linux wants to have the HWCursor Flag
in the x86config respectively xorgconf enabled. With the usual SW-Cursor
you will have "nice" distorted menues.

---

### Post by trellis on 2007-07-01
someone has reported the bug on launchpad

[https://bugs.launchpad.net/ubuntu/+source/blender/+bug/109217](https://bugs.launchpad.net/ubuntu/+source/blender/+bug/109217)

so hopefully get a fix soon

---

### Post by snoop on 2007-07-01
Its probably related to the ATI driver. I have run blender in ubuntu with no problems (intel video card).

Did you try using it in fullscreen mode instead of the windowed mode?

---

### Post by trellis on 2007-07-02
on mines it happens in  both windowed and full screen , it does seem to be an Ati problem

---

### Post by ETS_5005 on 2007-07-02
Same problem with Blender here. Run it but it is hopeless to use it.
Using ATI Radeon 9600.
Also what is it that Blender seems to disappear when I press Render? What is this?

Working in full screen is quite use-able and rendering within Blender enables rendering.

---

### Post by cyberkoa on 2007-07-06
I don't think this is  ATI specific problem, I am using Intel display , with Desktop Effect enable.

---

### Post by howlingmadhowie on 2007-07-26
i'm running a computer with a radeon mobility m6 ly and i have the same problem.

---

### Post by cyberkoa on 2007-08-06
I disable Desktop Effect , and the problem resolved. Therefore, confirm is the Desktop Effect conflict with Blender.

---

### Post by trellis on 2007-08-07
> **cyberkoa said:**
> I disable Desktop Effect , and the problem resolved. Therefore, confirm is the Desktop Effect conflict with Blender.

When you say disable , do you mean switching them off ? , for me switching them off does not resolve this problem ,

---

### Post by alterpinguin on 2007-08-07
dont know what you blame about 3d-blender-display:
i run:
=====================================
=  Blender 2.43 System Information  =
=====================================

Platform: linux2
========

Python:
======

- Version: 2.4.4 (#1, Apr 12 2007, 21:00:32) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)]
OpenGL:
======

- Renderer:   GeForce 6600/AGP/SSE2/3DNOW!
- Vendor:     NVIDIA Corporation
- Version:    2.1.0 NVIDIA 96.31

on Ubuntu 7.04, Feisty Fawn

i am shure there is no such distortion in display in window-mode - dont know in fullscreen, because i normaly only use window-mode
(i did use 2.41 and 2.42 too some time ago, but had not such problems)

---

### Post by KIAaze on 2007-08-07
Well, it's not because you don't have the display problem that it isn't there.

I have it with or without desktops effects enabled, with or without window mode.
And I don't seem to be the only one.

---

### Post by aen on 2007-08-09
This is not ATI specific. I have the same issue on both of my Dell XPS M1210 which run Intel 945GM video cards.

Non of the solutions I've seen anywhere have worked so far.

---

### Post by trellis on 2007-09-10
hello

well i managed to fix my problem , i have an  ati m7500 , i used this guide  to install ati drivers 

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

I already had the drivers installed , but i am guessing that this part of installation fix the problem


 Disable Composite Extension

In Ubuntu Feisty the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. In order to disable Composite you have to edit the xorg.conf file:

gksu gedit /etc/X11/xorg.conf

and add these lines at the end of the file:
File: /etc/X11/xorg.conf

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection


hope you find this helpful as i have

---

### Post by Red Moose on 2007-12-11
The problem is with the older ATI cards.  I had this problem when I had a Radeon 7000.  I had to downgrade the mesa drivers to 6.5.1, I think.

---


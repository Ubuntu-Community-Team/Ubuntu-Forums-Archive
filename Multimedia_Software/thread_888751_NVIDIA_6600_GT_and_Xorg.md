---
title: "NVIDIA 6600 GT and Xorg"
date: 2008-08-13
forum: Multimedia Software
---

### Post by jtrindle on 2008-08-13
I've been beating my head on this one for a while... though I finally got the GeForce2 MX 4000 running, and the 6200LE running OK, now I am trying a 6600GT.  Does anyone have the a snapshot of the proper configuration for this, or a guaranteed recipe for how to get there?

I've tried envy, and it wants to install driver version 173 and glx-new.  I've tried manually installing 96.xx and nvidia-glx.  In both cases, I can't get the restricted driver to load.  Xorg goes to VESA mode after it can't find a compatible NVIDIA driver.  

Which driver does the 6600 take?  Do I have to do anything special to make the driver load properly?

(why so many cards? I'm trying to get Second Life to run at a reasonable speed without spending a fortune on a new card.  I also have AGP and no PCI-E).

---

### Post by jtrindle on 2008-08-15
Update:

The main original problem was the need for Option "NoPowerConnectorTest" with the newer card.

In addition, at one point I got to see the full resolution, but after login I got a white screen.  Turns out, compiz.real was segfaulting.  Removing compiz-fusion packages fixed that.  I ended up with a full-resolution and color screen, but no restricted driver installed and no 3D acceleration (glxgears about 1100 FPS).  This was with the Envy install, using 173.

Now I'm back in version hell, with some approaches installing 96.xx, some 169.xx, and some 173.xx.  Often I'm in a spot where the kernel driver is different than the GLX module wants.  The "best" match was 169.xx in nvidia-glx-new, and 173.xx in the kernel. 

I can't seem to download 169.xx from NVIDIA directly.  Envy installs 173, and nvidia-glx-new seems to want 169.xx

Please, is there a current pointer to download the restricted driver support and 169.xx, or a way to get 173.xx installed in both the kernel and GLX??

thanks for any help.

---


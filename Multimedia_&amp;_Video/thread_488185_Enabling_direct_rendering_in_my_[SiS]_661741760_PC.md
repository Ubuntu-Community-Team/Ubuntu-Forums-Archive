---
title: "Enabling direct rendering in my [SiS] 661/741/760 PCI/AGP card"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by ferpadro on 2007-06-29
Hi everyone! The question is itself pretty obvious: is there a way to enable direct rendering in my card model. I heard that some versions of sis cards can achieve it, and some cannot. This is my lspci output (video card related line of it):

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

and i cannot even type in a terminal glxinfo | grep direct coz it freezes one second and then takes me back to login screen. Whenever i do a glxgears command the wheels start spinning relatively fast at the beggining, but after the first second they start to spin very slow or sometimes they don t spin at all. 

Is there any way of enabling direct rendering? not only to install eye-candy applications. but also to improve my windows scrolling being more smooth that what it is now.

Regards

---

### Post by blairafon on 2007-07-03
i would like to know the answer to that too my identifier is

Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by jeremybubs on 2007-07-09
hello, i have been looking all over for a solution also.  i have the same exact identifier for my video card, and i cannot seem to enable direct rendering.

the same exact thing happens to me when i run glx gears, great for a few seconds, then almost not moving at all.

any help would be great!

---

### Post by mightyzug on 2007-07-21
i am in the same boat, last thing on my checklist of things to fix  :)

---

### Post by jeremybubs on 2007-07-25
quite a few people with the same problem... its interesting that theres nothing on the internet about this.

---

### Post by dan-arwed on 2007-07-29
Hi all, I have the same question, lspci giving

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

Any help appreciated =)
Best regards
Dan

---

### Post by matogrosso on 2007-08-15
Hello,

According to:
[http://www.winischhofer.net/sisdri.shtml](http://www.winischhofer.net/sisdri.shtml)

There is no DRI support for the SiS 315/550/650/651/740/661/741/760/330.

I'll try some of the drivers in that webpage when I find some time and will let you know. Or if you come across a solution before I do, please let me know.

I posted the following thread:
[http://ubuntuforums.org/showthread.php?t=524799](http://ubuntuforums.org/showthread.php?t=524799)

Cheers,
Matogrosso

---

### Post by jeremybubs on 2007-08-21
does that mean it is not possible for it to work on our graphics card, or simply a driver has not been written yet?

---

### Post by matogrosso on 2007-08-22
Jeremybubs,

Yes and yes. DRI does NOT work for our SiS cards and the reason is the fact that there is no driver for them. And it looks like there won't be any drivers, because the company (SiS) does not care about linux users. I have dual boot at home, so I use windows when I want google earth or supertux. The graphics on windows is better than in Linux (because a driver exists for windows) but it not great. I'll leave it as it is for the time being and will consider buying a video card in the future. Maybe that is the best people in our situation can do.

---

### Post by jeremybubs on 2007-08-27
thanks... maybe if i learn more, i could write a driver myself.

---

### Post by elinav on 2007-09-01
Hi,

I found that SiS does have a linux driver (RedHat). 
Can this bring any solution?

I have: SiS 65x/M650/740 PCI/AGP

Doron

---

### Post by michael37 on 2007-09-29
From the same page,
> 
# DRI ("Direct Rendering Infrastructure") is the basis for OpenGL and hardware 3D acceleration. Without DRI, X.org/XFree86 will use software rendering for OpenGL and 3D which is really slow.
# The X driver this page is about has nothing to do with DRI. Instead, a separate driver is needed for this feature. This separate driver is developed by the DRI developers. I do not do any DRI related development, hence asking me questions about DRI is useless (and such questions won't be answered).


More info about DRI is [here](http://dri.freedesktop.org/wiki/).

---

### Post by john_spiral on 2007-11-10
FYI

I had the same problem in 7.4 but after an upgrade to 7.1 I'm able to run **glxinfo** without being thrown back to the login screen.

If you wish to stick with 7.4 you might need to update **xserver-xorg-core** to a later version.

7.4 has the below version of xserver-xorg-core:

xserver-xorg-core 2:1.2.0-3ubuntu8

7.10 has the below version of xserver-xorg-core:

xserver-xorg-core 2.1.3.0.0.dfsg-12ub 

I've got the following graphics card:

Silicon Integrated Systems [SiS] 741/741GX/M741

hope this helps

John

---


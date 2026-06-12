---
title: "[SOLVED] Nvidia and glx"
date: 2007-11-21
forum: Mythbuntu
---

### Post by mrkite00 on 2007-11-21
Hi all.

I just upgraded my mythtv box with an nvidia geforce 6200 instead of an old ATI.

My problem is that any opengl call makes X crashes. Like opening MythTV or just calling glxinfo.

I searched around and I think I have found the problem but I don't know how to solve it yet.

In Xorg.0.log, I have these lines:
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

Up in the same log, I see those lines:
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"

So I think that the glx module loaded should be the one that ship with  the nvidia driver and that's what causes the problem. 

When I installed the card, I think I installed nvidia-glx manually with apt-get. After that, I uninstalled all that (including restrited module packages), logged in in safe X mode, fired up restricted driver manager which installed nvidia-glx-new and a couple of other packages.

Somewhat, it looks like something is still not right. Running the following command:
ls -l /usr/lib/xorg/modules/
yields that libglx is a link to:
libglx.so -> libglx.so.100.14.19 (which looks nvidia to me...)

So, could anyone 
1. confirm that on their Xorg log file, the glx module loading is the nvidia one
2. Explain how I would make that module load

Thanks a lot! :)

---

### Post by mrkite00 on 2007-11-23
Hi. I've fixed this by installing manually the driver, downloaded from nvidia.

Not really a nice solution if you ask me, since I had to install gcc, linux headers, libc headers and so on. I imagine any linux newbie would not have gone that way...

But I just figured out that in my last post, I had the path for the glx extension, which is in /usr/lib/xorg/modules/extensions/ instead of /usr/lib/xorg/modules (where I was looking...). Now, the libglx in /usr/lib/xorg/modules/extensions/ is a link to the nvidia glx module instead of a plain X module.

Could probably have done the link there myself if I had been more clerver!:popcorn:

Thanks

---


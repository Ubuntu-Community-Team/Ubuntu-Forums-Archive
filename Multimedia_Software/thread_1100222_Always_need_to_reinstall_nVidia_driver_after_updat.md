---
title: "Always need to reinstall nVidia driver after update"
date: 2009-03-19
forum: Multimedia Software
---

### Post by Derek_ on 2009-03-19
I have an nVidia card, and it works perfectly.  I use the technique of manually installing the nVidia driver from their website.

My problem is that whenever I run the software updates, or at least very often when I do, the updates misconfigure my video, often to the point of being unusable.  Ctrl-Alt-F1 and re-running nVidia's driver installation fixes it completely, but it's annoying to have to do that every time.

Is there some way to keep the updates out of my video settings?  Do I need to check the update packages for xorg and unselect those?  Or can I safely just lock the affected files somehow?  I can't be the only one who goes through this, so maybe someone has a good solution?

---

### Post by norwoods on 2009-03-19
drivers installed with envyng or from a repository like [www.avenard.org](www.avenard.org) typically function after updates.  i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

### Post by Derek_ on 2009-03-19
> **norwoods said:**
> drivers installed with envyng or from a repository like [www.avenard.org](www.avenard.org) typically function after updates... 

Thanks.  But I'm reluctant to experiment.  I'm hoping for something more deliberate.  My driver and config are good as-is, and I just want to keep them from being changed.

---

### Post by roblubbers on 2009-03-19
Well, that is close to impossible if you use the nvidia drivers & installer from the nvidia website. The only thing you can do is never update the kernel. Because the problem lies in the combination of nvidia drivers and kernel. If you just use the drivers from the ubuntu repo's the drivers also get updated if the kernel get's updated and you won't have any problems at all. Otherwise you will just have to reinstall the drivers after each kernel upgrade.

---

### Post by Npl on 2009-03-20
The driver is not the problem (well... almost never is), the reason your system breaks down is that the kernel-module and kernel must match. 
You can setup Linux to automatically detect new kernels and compile a new kernel-module as needed, one way to do this is laid out in [this tutorial]("http://ubuntuforums.org/showthread.php?t=1036788")

---

### Post by Derek_ on 2009-03-20
> **roblubbers said:**
> ...Because the problem lies in the combination of nvidia drivers and kernel...

Thanks, roblubbers and Npl.  Exactly what I needed to be told.  I don't know why that basic issue didn't occur to me.  The nVidia installer is recompiling it every time for a reason.

So I can either automate the recompiling step or get my driver updated from a source that stays in sync with the kernal updates, which would be the more standard method.  I got away from using the ubuntu repository for my video driver because it wasn't working.  But maybe I will try again (that was back with 7.04) or look into that link from Npl.

---

### Post by Derek_ on 2009-03-20
> **norwoods said:**
> drivers installed with envyng or from a repository like [www.avenard.org](www.avenard.org) typically function after updates

This makes more sense to me now that the other two straightened me out.  Thanks.

---


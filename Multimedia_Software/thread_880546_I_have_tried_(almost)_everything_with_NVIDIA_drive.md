---
title: "I have tried (almost) everything with NVIDIA drivers."
date: 2008-08-05
forum: Multimedia Software
---

### Post by tetrafuran on 2008-08-05
What else is there left for me to do? I've read so much that I cannot imagine what to do next. I've followed several guides, helps, howtos and threads.

Stuff I've already done
1. in boot I see the screen and graphics preferences. I select nv - nVidia Riva, geforce etc drivers. The programs forgets the settings as soon as I click ok.
2. Try the same after booting X in low graphics mode. gksudo displayconfig-gtk gives me the same menu and I did the same thing and got the same results. (i.e. no results)
3. I tried gksudo nvidia-settings. It says that I'm not using nvidia X drivers
4. I tooke the advice to use nvidia-xconfig. xorg.conf got remade. so what.
5. returned to step 3 and I'm still getting the same errors. 
6. perform a manual check: System - Administration - Hardware Drivers. I enabled the drives.
7. nvidia-settings still hasn't changed it's mind about the drivers. Still the same errors.
8.envyng-gtk actually downloads and installing someting!!!!! 
9. After reebooting I'm back to square 1. It's using some vesa drivers and therefore unable to display better graphics.
10. I read more "solutions" from ubuntu forums.
11. After playing around with steps 1-10 for a while I somehow managed to get some results in the "hardware drivers" windows. Now it says the drivers are enabled, but not in use.

---

### Post by cdtech on 2008-08-05
Have you tried going into the "Synaptic Package Manager" and click on "Search" type in "nvidia" and install:
```
nvidia-glx-new
nvidia-kernel-common
nvidia-new-kernel-source
nvidia-settings
```
Be sure those are installed.

Also be sure your "/etc/X11/xorg.conf" file has:
```
Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection
```

Also be sure your "System > Administration > Hardware drivers" has the graphics checked.

Hope this helps............

---

### Post by xc3RnbFO8P on 2008-08-05
And **xserver-xorg-video-nv**

---

### Post by cdtech on 2008-08-05
> **Ringi said:**
> And **xserver-xorg-video-nv**

woops, forgot about that one.
I have the xserver-xorg-video-v4l

---

### Post by tetrafuran on 2008-08-05
nvidia-glx-new
nvidia-kernel-common
nvidia-new-kernel-source
nvidia-settings
Some of these (ofcourse) are not installed since I used envyNG. It uninstalled those and put it's own stuff in it's place. But I suppose there's no harm in going back to old style. I can't really remember if they where there in the first place. 

In any case I installed the stuff you asked and added "v4l" to xorg.conf. After that I got greater resolutions. Thanks. Now I'll still have to test 3d and video performance.

I haven't installed xserver-xorg-video-nv yet. The lack of it does not appear to affect desktop performance.

---

### Post by tetrafuran on 2008-08-05
OK. Now I've installed some 3d games. I also re-checked that all the packages mentioned here are installed.

As I start any of those games, I just get a black screen for less than a second and the thrown back to the desktop.

In any case adanaxisgpl gives and error related to sdl video mode failing and not being able to select a compatible video mode.

Armagetronad on the other hand talks about matching GLX visual whatever. So far I'm happy with the resolution. Let's see what happens if I reboot.

[after the reboot]

Never mind about the games. We're back to displayconfigure-gtk not remembering mys settings.  During start up I was greeted with 640*480 resolution, but at least it was using the nvidia driver.

Now after playing with settings and my previous tricks that I mentioned earlier, we're back to square one. Next i'll start trying out how envyNG is able to help.

Here's a list of installed items with the keyword nvidia:
envyng-core
envyng-gtk
jockey-common
jockey-gtk
linux-restricted-modules-2.6.22
linux-restricted-modules-2.6.24
linux-restricted-modules-2.6.24
nvidia-gc-toolkit
nvidia-glx-new
nvidia-kernel-common
nvidia-new-kernel-source
nvidia-settings
smartdimmer
xserver-xorg-video-nv

At the moment I'm beginning to think something needs to be uninstalled. Any ideas? I remember that last time this happened, I reinstalled ubuntu. I've learned that ubuntu owners should never ever touch their GPU's. ever. If it works, let it be. Every time I changed that card, something awfull has happened.

---

### Post by tetrafuran on 2008-08-07
Apparently this nvidia driver issue cannot be solved. Therefore I took another hard drive and installed a fresh new hardy. The drivers worked, but the system just happens to crash all the time. Apparently long and troublesome way didn't work. The quick and dirty solved the issue, but brought in another one which was ever worse.

Yesterday I downloaded openSUSE DVD.

---


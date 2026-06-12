---
title: "[SOLVED] nvidia-settings reports not using nvidia driver--but I am!"
date: 2008-05-28
forum: Multimedia Software
---

### Post by madscientist on 2008-05-28
I have Ubuntu 8.04 installed and I have an nVidia NV44 [Quadro NVS 285] card.  I've installed the proprietary drivers and they seem to work fine.  Now I want to set up dual monitors (both are almost identical LCD's so this should be very easy).

I've read most people are using nvidia-settings for this, so I installed that package (I've read some older posts saying this comes included in the nvidia-glx-new package, which I'm using, but that's not true anymore: there is a .png for that app but not the app itself).

After installing I see System->Administration->NVIDIA X Server Settings, but when I click it (or if I run "gksudo nvidia-settings" I get an error dialog that says > You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.and I get a tiny window for NVIDIA X Server Settings with no options except "Help" and "Quit".

However, I *have* run nvidia-xconfig, and I'm most definitely using the nvidia drivers (I see the nvidia splash screen when X starts).

I have no idea why I can't run nvidia-settings: help!!

---

### Post by briandu on 2008-05-28
If you follow [http://ubuntuforums.org/showthread.php?p=5064980#post5064980](http://ubuntuforums.org/showthread.php?p=5064980#post5064980) msg #430 it should get you going and my nvidia control setting works (as part of the install).

Perhaps you missed a step somewhere?

---

### Post by madscientist on 2008-05-29
Hrm.  I was hoping to just use the default packages from Ubuntu.  They do WORK, as in I can use the nvidia driver and everything works.

I just can't use nvidia-settings.  I'm not sure throwing out the packages for a self-install is worth it to get nvidia-settings running.

Thanks for the pointer though: I'll think about doing this just to see if it fixes my problem.

---

### Post by madscientist on 2008-06-05
OK, I decided to take another stab at this today, and after reading various other threads and trying lots and lots of different things in my xorg.conf file, I finally got it working.

First, I discovered that "glxinfo" reported "direct rendering: no" which is obviously not right.  However, none of the fixes I tried resolved this issue... UNTIL I discovered a post saying:

"Removing the xserver-xgl package fixed it for me"

Well, I removed that package and BANG!  I get "direct rendering: yes" from glxinfo, and nvidia-settings works now, and best of all (this was the real goal for me) nvidia's Xinerama reporting is now working properly so that the window manager realizes I have two screens and handles them properly: before my screens looked like one big screen to the WM so my panel etc. was extended across both screens AND things like window maximize would use both screens, dialogs would appear split across both screens, etc.

I don't know what it is about that package being installed but removing it fixed ALL my problems.

One odd thing, though: after I removed that all my xterms (I use those instead of gnome-terminal) appeared with black background and white foreground, instead of the usual white background/black foreground.  I used ~/.Xresources to fix that but it's very odd since the only thing I changed was removing xserver-xgl!

---


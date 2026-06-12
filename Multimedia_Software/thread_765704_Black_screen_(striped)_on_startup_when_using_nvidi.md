---
title: "Black screen (striped) on startup when using nvidia drivers in Hardy"
date: 2008-04-24
forum: Multimedia Software
---

### Post by puller on 2008-04-24
Hi everybody!
I have an Ispiron 1520 Notebook with an nVidia 8400M GS video card.
I just installed Ubuntu Hardy 8.04.
I enabled the nvidia restricted drivers, and when i rebooted the system i had an irregularly colored black screen (similar to black stripes of ink).
On the background i could ear the drums, and if i write my username and password i can ear the ubuntu log-in theme, so the system starts, but with no image on the monitor (except the vertical black stripes)!
If i wait some time, the black stripes become thicker and more defined, and at the end, it remains only one stripe on the middle-right of the screen, and the rest of the screen is white.

I was able to make it work again using the terminal (ctrl+alt+f1) and editing my xorg.conf file, replacing "nvidia" with "nv" as the video card driver.

Changing this makes it working, but it is a pain: scrolling pages with firefox, or moving windows in Gnome is jerkily! So i need to use nVidia drivers!

Could anyone help me to have it working?

Here's my xorg.conf.
Thank you.

---

### Post by puller on 2008-04-24
I forgot to say that i also tried with envy and had the same issue!
Changing again nvidia to nv in xorg.conf, brought me back the x-server, but again with painful scrolls on firefox, and slow window movements!
Bye.

---

### Post by puller on 2008-04-25
Please, someone help me, in this state my pc is not usable!
I need the nvidia driver to work!
Thanks.

---

### Post by puller on 2008-04-25
I found a working solution here:
[http://www.nvnews.net/vbulletin/showthread.php?t=107138](http://www.nvnews.net/vbulletin/showthread.php?t=107138)

Used phoenix edid in windows, exported the edid in raw format and included it in the xorg.conf as described in that thread!
Bye.

---

### Post by nirudha on 2008-04-25
Try removing the nvidia-glx(-new) drivers (via synaptic or some other package manager) and also adding NV to the blocked restricted module list. Then do the installation of the driver package you downloaded from Nvidia.

[http://ubuntuforums.org/showthread.php?t=766489](http://ubuntuforums.org/showthread.php?t=766489)

Hope that helps.

---

### Post by Kyle138 on 2008-05-07
Dude, Puller, Thanks,

I held off upgrading my laptop to hardy because I use it for work and was terrified it would have problems. Sure enough, upgraded, rebooted, scrambled. I've been fighting this almost 10 hours now, I've rebooted so many times I've seen the fsck twice, I've tried EVERY suggestion across 3 forums, and the link you posted about the EDID finally fixed it.

So Thanks to Puller for finding the link,and thanks to those guys for finally figuring it out, and CURSES TO THE DEVS!!! Seriously? NO ONE at canonical was using nVidia drivers?

---


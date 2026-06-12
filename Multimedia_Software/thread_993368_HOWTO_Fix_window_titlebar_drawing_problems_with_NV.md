---
title: "HOWTO: Fix window titlebar drawing problems with NVIDIA gfx using 180.08 beta driver"
date: 2008-11-25
forum: Multimedia Software
---

### Post by ryukent on 2008-11-25
OK, as of today the latest NVIDIA drivers are 177 in the repos. This causes a bug with the new Intrepid Kernel causing the window title bars on some systems to draw incorrectly. It tends to be an intermittent problem. This is a temporary fix using the NVIDIA 180.08 beta drivers.


Go to:
[http://www.nvnews.net/vbulletin/showthread.php?p=1847941](http://www.nvnews.net/vbulletin/showthread.php?p=1847941)

Download the file you need for your architecture. It's NVIDIA-Linux-x86-180.08-pkg1.run for x86. 

Close all applications and save everything.

CTRL+ALT+F1.

Log in. Then run "sudo /etc/init.d/gdm stop" to kill you XWindows session.

Go into the directory where you put the driver and run

"sudo sh NVIDIA-Linux-x86-180.08-pkg1.run" or the relevant command if you downloaded the 64-bit version.

It will try to download a module, then ultimately recompile a new one.

When you log back into XWindows, the new driver should be active and the window drawing problem gone.

Hopefully NVIDIA will release a finished driver that will find its way into the repos soon.

If you want to go back to you old driver, you can do it using System / Administration / Hardware Drivers. It will still display the old one active in there, just swap to a different one, activate it, then swap back.

Good luck!!

---

### Post by ademey on 2008-11-26
Thanks a lot for this posting. A bit "tricky" for someone only used to GUIs, but seems to work. Which is great!

Andreas

---

### Post by TunaCanTommy on 2008-11-26
The "twitchy" artifacts in the window titlebars was bothering me too.
Your post worked fine and fixed it for me . . very simple, very easy.
Just a small addition for those (like me) not too used to using the command line in a Terminal.
To get XWindows running again you log back into XWindows with:
```
sudo /etc/init.d/gdm start
```

One question: When I go to SYSTEM > Administration > Hardware Drivers
it shows I still have nVIDIA Driver ver 177 "activated" . .  should I deactivate it now that I have ver 180.08 installed ? ?

Edit:  Just re-read your post.  The old drive stay "active", and as you say - to use it again, just active one of the others listed and then go back and re-activate the ver 177 driver - thanks again.  Good info :)

---

### Post by johneboy on 2008-11-28
Thanks Ryukent, that worked fine for me too.  

I had an issue following the kernel update this morning, this caused my laptop to boot into safe graphics mode.

The fix was to just follow your instructions again to rebuild the driver for the new kernel and it is now working correctly again.

Cheers

John

---

### Post by ryukent on 2008-11-28
Yes, I had that problem too. Because the install script compiles a module for the specific Kernel you're running, if you update the Kernel, you need to run it again to recompile a new one. Hopefully this will be sorted when the official driver is released in the repositories.

---

### Post by abdulwahed on 2008-11-29
after compiling the driver , system failed to start with the last driver and its working with low graphic mode.
i switch to version 177 then restart but the same happend again.
is it any way to remove the version 180 from the system and get back to the old configuration.

---

### Post by kamitsukai on 2008-11-29
I'm getting a slight problem...

when I type 

```
sudo sh NVIDIA-linux-x86-180.08-pkg1.run
```

it tells me:

```
Sh: couldn't open NVIDIA-linux-x86-180.08-pkg1.run
```

or something similar anyway
[B][U]
EDIT:[/U][/B]

Missed out the capital letter from _L_inux:lolflag:

---

### Post by ryukent on 2008-11-29
Abdul - you can run it with --uninstall to uninstall, but it probably won't uninstall it properly. The problem might have been caused by an updated Kernel. Have you tried just running it again and making sure that you let it create a configuration file (one of the last options)???

If not, try 

Removing all nvidia packages (except for xserver-xorg-video-nv). Then restart. It should run the default X.Org nvdia driver. If you still have problems or want to run 177 (with the bugs bugs), in synaptic, mark libgl1-mesa-glx for force reinstall.

Then at the command prompt, run

sudo rm /usr/lib/nvidia/libGL.so.1.2.xlibmesa
sudo apt-get install nvidia-glx-177

That should take you right back to the dodgy 177 driver.

---

### Post by abdulwahed on 2008-11-29
i recompile again with the new kernel, its working perfect now.
Thanks a lot

---

### Post by rynop on 2009-01-03
Just an FYI. I tried to use the 180.18 drivers (newer ones) and I had tons of problems loading the nvidia driver.  

I decided to try 180.08, and it works perfectly.  So stick with the .08 for the time being. Hopefully this saves someone some time.

---

### Post by ballin on 2009-01-06
works a charm, many thanks!

---

### Post by Jole on 2009-02-26
Great fix. thanks a lot. No more anoying window gliches ;-)

---


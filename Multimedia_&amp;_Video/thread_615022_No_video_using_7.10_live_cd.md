---
title: "No video using 7.10 live cd"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by hlgcis on 2007-11-16
I'm trying to do a fresh install of 7.10 and I run into a problem where it boots up all the way but right after it activates X the video/graphics stops working and my monitor goes to sleep. Ubuntu is still running in the background and the startup sound does its thing but no video works.
I've tried all of the video options from the boot menu and none of them seem to work.
I'm using the i386 iso image on a computer with an nVidia Geforce 660 card (256 mb), AMD Athlon 64 3200+, 1 GB RAM.
Are there any text mode commands that will make it work so that I can install it to the hard drive and get the proprietary drivers installed?
Thanks

---

### Post by integr8e on 2007-11-16
There may be an error(s) on the CD you have.  When you first boot your computer, choose the option "Check CD for defects".  If it doesn't show any errors detected, you may want to just use the Alternate Install CD, which allows you to install *buntu without the GUI.  You can also try running the following command from the command line:
```
sudo dpkg-reconfigure xserver-xorg
```

Choose "nv" (or "vesa" if that gives you trouble) as your video driver and select the defaults for everything else.  When you get to the option that allows you to select what resolutions you want to include with the configuration, use the Space bar to (de)select the options you desire, making sure not to include anything more than your monitor can handle.

---

### Post by hlgcis on 2007-11-16
I verified and everything was OK and I decided to give safe graphics a try again and for some crazy reason it worked this time.
I'm installing from the GUI now.

---

### Post by integr8e on 2007-11-17
>  . . . and for some crazy reason it worked this time.

Great!  Let me know how it all works out.

---


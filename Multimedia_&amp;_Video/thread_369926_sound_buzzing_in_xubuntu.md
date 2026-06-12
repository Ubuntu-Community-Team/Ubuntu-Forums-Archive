---
title: "sound buzzing in xubuntu"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by skipo on 2007-02-25
I installed xubuntu 6.10 to an old HP Omnibook xe3 laptop.  When you use headphones you can hear buzzing in the sound, which gets worse when you use keyboard or touchpad.

Can I do anything to get rid of this buzz? it's really annoying.

---

---

### Post by Co.Sinecure on 2007-05-20
I have a similar problem in Feisty. 
I've used previous versions of ubuntu (6.06, 6.10) using the standard Gnome install without a problem, but this install I removed all the ubuntu-desktop packages to try out some other window managers, and I didn't notice a problem until I uninstalled...so could it be something in the gnome install? As far as I can tell I have ALSA installed, and I also installed esound. I'll try uninstalling both of those to see if it makes a difference...

--Edit
Some URLs which probably won't help:
[heatsink/fan mod]("http://daveluna.com/blog/?entry=20070424_782_5481_4668675321.html")
[forum.notebookreview][NX6110 High Pitched Buzzing]("http://forum.notebookreview.com/showthread.php?t=32067")
[forum.notebookreview][High Pitched Noise is Killing Me]("http://forum.notebookreview.com/showthread.php?t=15682")
Now after skim-reading that last link, I closed the lid of my laptop - the buzzing stopped! Reopened, no buzzing *until* the LCD screen dimming kicked in...Why Is It So?

--Edit #2
So removal of alsa/esound did not have an effect.
Also, The sound kicks in on startup when in loads up hardware drivers.
Did an 'lshw' and found the vendor name for my video card, 'Trident Microsystems'. Checked that the associated package xserver-xorg-video-trident was the latest version, it was. No joy so far :(

---

### Post by skipo on 2007-05-20
I'm now using fluxbuntu, but the buzzing still continues with the headphones. I just remembered that I had similar issues with my desktop computer. It's an old AMD Athlon and if I use athcool for powersaving and the integrated soundcard I get same kind of buzzing. I solved that problem with new soundcard.

I wonder if this also has something to do with powersaving?

---


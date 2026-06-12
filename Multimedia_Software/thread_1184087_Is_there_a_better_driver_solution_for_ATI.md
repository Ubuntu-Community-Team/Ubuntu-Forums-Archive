---
title: "Is there a better driver solution for ATI?"
date: 2009-06-10
forum: Multimedia Software
---

### Post by sloppyc on 2009-06-10
I'm using the drivers drom the ATI site; Catalyst 9.5.  It's not bad, but I find it somewhat limited in multiple monitor features.  

I finally got resolutions set the way I like (this didn't happen right away), and now I can't change the primary monitor.

I have a Gigabyte 780G motherboard (MA78GM-US2H) with integrated RadeonHD 3200 graphics.  It seems that no matter what I do, the DVI (or HDMI) screen is detected first and treated as the primary screen.  GDM login screen displays there, panels did by default, and often enough to force me to consider Windows as the primary OS for this HTPC, messages and applications open up there.  I even tried looking in the BIOS for an option to set the primary screen.

I need everything to open on the VGA-connected screen.  If I'm watching a movie, I'll drag VLC over to the other.  This shouldn't be a big deal.  It's a complete non-issue with Nvidia's nvidia-settings (or Windows, natively).  It would be a non-issue if I could use two DVI ports on th graphics card as well, but I have to use either VGA+DVI or VGA+HDMI.


My xorg.conf is in [this thread]("http://ubuntuforums.org/showthread.php?p=7396577#post7396577") that was ignored in Beginner Talk  :(

I've tried aticonfig --swap-screens and it seems that nothing happens, even after a reboot.
I've tried --swap-monitor and it tells me it can't do anything with XRandr1.2 enabled.

Ideas?  I'm about to nuke my Ubuntu partition.

---

### Post by ssri on 2009-06-11
You can disable xrandr to allow catalyst to setup multiple monitors in amdcccle...

here's the post that explains it:

[http://ubuntuforums.org/showthread.php?t=1171926](http://ubuntuforums.org/showthread.php?t=1171926)

---

### Post by sloppyc on 2009-06-12
That looked promising for a minute; I can now enable BigDesktop in the Control Center.  But now I'm in the same position as before (well, slightly better; BigDesktop is a little better than Xinerama, from what I can see so far).  Slight progress.

GDM still opens on the left-hand screen, which I do not want.  Can't I just configure GDM somewhere to open 1920 pixels to the right?

The weirdest thing is that the display I want to be the primary always is identified as "1" in the control center.


[[img]http://www.imagejar.com/site/pic/925PekA/4241.jpg[/img]](http://www.imagejar.com/site/pic/925PekA/4241.jpg)

---


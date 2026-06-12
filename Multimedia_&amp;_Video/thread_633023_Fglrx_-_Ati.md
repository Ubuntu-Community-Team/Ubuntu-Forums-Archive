---
title: "Fglrx - Ati"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by Gorlist on 2007-12-06
Hi, currently running fglrx for my Radeon, though use to use proper ATI drivers in previous incarnations of Ubuntu - problem is ive noticed using fglrx in 7.10 its not quiet as responsive, but its a throw up on whether I really want to go through the hassel and risk of trying to get offical ATI drivers functioning or stick with what ive got.

So, if I do install proper ATI drivers, whats the accepted route for doing this in .10, considering theirs now the restricted manage program and new Screen and Graphics GUI.

Regards :)

---

### Post by ycason on 2007-12-06
Fglrx is the name of the official drivers.  The open-sourced ones are called radeon.  :)

---

### Post by Gorlist on 2007-12-07
:) theirs also another set of drivers from ATI?

what are the opensource set like?

Regards,

---

### Post by acoustibop on 2007-12-07
AS ycason says, the fglrx drivers are ATI's "official" proprietary ones.  Aside from radeon, there's also the ati driver; these are both free drivers.

If you just want a driver that will speed things up a bit - but lose you things like Compiz if you're using them - just open the Restricted Drivers Manager, tick the box, click OK (or whatever), let it download and install the driver and reboot when instructed.  That will install the fgrlx driver in the repositories (currently 8.37.6) with no hassles.

Or, if you want the latest driver, which now supports composite and AIGLX, and with which you can run desktop effects such as Compiz produces, go to one of the fglrx how tos - I'd recommend the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") - and follow the instructions for Gutsy - or whatever version you're using.  This will include the location to download the driver.

The Unofficial Wiki for the ATI Linux Driver works perfectly for me.  However, it is more likely that you will get installation and running issues this way than with the Restricted Drivers Manager way.

Incidentally, you don't say what Radeon card you have, but ATI's release notes say you need a 9500 or better for either of the above fglrx drivers.

---

### Post by Gorlist on 2007-12-07
Running a 1950x 

Right understand now! no don't use Compiz so doesn't really matter, already running fglrx. Just the desktop doesn't seem as poky as previous releases.

Short of some stuck Gnome Menu manager entries its work great.

Regards,

---


---
title: "Display flickering after upgrading monitor"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by akolliop on 2006-08-14
I used to be running two monitors at 1280x1024 and 1680x1050, but I just upgraded the 1280x1024 to also be 1680x1050.

The new monitor is on an analog connection (the other uses DVI), and it won't let me select anything other than 75 Hz for the refresh rate, which is odd, because the monitor is running 60 Hz on the DVI connection from a Windows box. It only flickers in response to some activity on either screen (if I just leave it there without opening anything, it's fine). The older monitor has no flickering at all. I just upgraded yesterday, and didn't notice any problems until I replaced the VGA cable today (I had to use a KVM switch as an extender to get the monitor to reach the Linux machine yesterday). Going back to the old cable set up has the same problems though.

Here is a short video demonstrating the problem: [380 KB]("http://kcomplex.com/storage/ubuntumonitortrouble.avi")

I didn't see any other threads that sounded quite like this sort of problem, so any help or ideas will be appreciated. Thanks!

---

### Post by tseliot on 2006-08-14
Configure your monitor:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by akolliop on 2006-08-14
Of course it was something really stupid, in xorg.conf I didn't have the name on the modes in the screen section matching the name on the modeline in the monitor section. Changing that fixed everything, running at 60 Hz now. Thanks muchly for the link that helped me notice the discrepancy!

---


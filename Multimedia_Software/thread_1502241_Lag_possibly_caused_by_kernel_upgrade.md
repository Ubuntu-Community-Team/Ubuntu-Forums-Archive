---
title: "Lag possibly caused by kernel upgrade"
date: 2010-06-05
forum: Multimedia Software
---

### Post by Sirron on 2010-06-05
My kernel is now 2.6.32-22 following an update.

Unfortunately I now experience a random lag; occasionally the mouse stops moving momentarily and any music I have playing skips a little.

It only lasts for a fraction of a second but freehand drawing whilst listening to music is now a frustrating experience.

I've put this in the Multimedia & Video forum because I suspected it would be a graphics card thing and it looks like I'm right; I use the proprietary Nvidia driver and after I uninstalled it and rebooted the problem was gone.

I need the proprietary driver because the open source one doesn't support my monitor's native resolution.

For now I've reinstalled 2.6.32-21 and that's fine with the proprietary driver, no lag at all.

So is this a kernel regression or what? How can I solve this?

Thanks!

(Clearly it's unwise to carry on using an old kernel forever)

---

### Post by ajgreeny on 2010-06-05
> **Sirron said:**
> My kernel is now 2.6.32-22 following an update.

Unfortunately I now experience a random lag; occasionally the mouse stops moving momentarily and any music I have playing skips a little.

It only lasts for a fraction of a second but freehand drawing whilst listening to music is now a frustrating experience.

I've put this in the Multimedia & Video forum because I suspected it would be a graphics card thing and it looks like I'm right; I use the proprietary Nvidia driver and after I uninstalled it and rebooted the problem was gone.

I need the proprietary driver because the open source one doesn't support my monitor's native resolution.

For now I've reinstalled 2.6.32-21 and that's fine with the proprietary driver, no lag at all.

So is this a kernel regression or what? How can I solve this?

Thanks!

**(Clearly it's unwise to carry on using an old kernel forever)**
If I were you I would not worry about that small problem.  Stick with the kernel that works for you and use the pin facility to stop the newer kernel keep appearing in the update notifier.

 To pin a package version add these lines to  /etc/apt/preferences:
Package: name               
Pin: version (number from repos)    
Pin-Priority: 1001

---

### Post by Sirron on 2010-06-05
Ok, will do.

---


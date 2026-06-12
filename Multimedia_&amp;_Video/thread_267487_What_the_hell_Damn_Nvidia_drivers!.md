---
title: "What the hell? Damn Nvidia drivers!"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by jpe2000 on 2006-09-28
I restart my computer and it says that there's a problem with the X server. THIS HAPPENS EVERY TIME I TRY TO INSTALL NVIDIA DRIVERS ON UBUNTU! Why is it doing this? Please help me!!!!

---

### Post by jpe2000 on 2006-09-28
Anyone?

---

### Post by enopepsoo on 2006-09-28
What is the problem that it reports?

I did a bad setup once and needed to restore my old xorg.conf to get back into X.

if it boots you into a CLI, try

```
cp /etc/X11/xorg.conf_[press tab] /etc/X11/xorg.conf
```

and press tab where it says [press tab];)

---

### Post by jpe2000 on 2006-09-28
Well, I tryed booting the live CD and AS ALWAYS (or most of the time) it locks up when it says 19 seconds left or whatever. It never did this to me? I have an order of Ubuntu disks. Would that help?

---

### Post by enopepsoo on 2006-09-28
If you do what I said it will restore your old configuration.  There will be no need to trifle with cds.

Once you have that done I suggest installing your nvidia driver with the envy script.  It worked wonderfully for me.

---

### Post by tseliot on 2006-09-29
> **jpe2000 said:**
> Well, I tryed booting the live CD and AS ALWAYS (or most of the time) it locks up when it says 19 seconds left or whatever. It never did this to me? I have an order of Ubuntu disks. Would that help?

It sounds like a hardware issue...

Does Ubuntu (the installed version) lock up like the livecd?

---

### Post by jpe2000 on 2006-09-29
Nope, it NEVER does. I have even checked the CD for scratches and the scratches on the CD shouldn't be bad enough to do that because 1 out of 10 I am able to get it installed without anything going wrong. Would the "ShipIt CD's" work?

---

### Post by tseliot on 2006-09-29
> **jpe2000 said:**
> Nope, it NEVER does. I have even checked the CD for scratches and the scratches on the CD shouldn't be bad enough to do that because 1 out of 10 I am able to get it installed without anything going wrong. Would the "ShipIt CD's" work?

I wouldn't know.

BTW you can follow this guide to install the Nvidia driver:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

or try Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by jpe2000 on 2006-09-29
Could it be my DVD drive going bad? Eventhough it only does this with the Ubuntu CD. I installed it on my dad's computer (because I have no clue how I convinced him to try Linux) and it worked the first time.

Thanks to all with the fast responces.

---

### Post by BLTicklemonster on 2006-09-29
> **tseliot said:**
> I wouldn't know.

BTW you can follow this guide to install the Nvidia driver:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

or try Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I highly recommend using Envy. Why go through all the gobbledygook if you don't really have to?

---


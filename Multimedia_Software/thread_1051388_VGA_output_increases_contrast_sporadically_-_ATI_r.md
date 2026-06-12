---
title: "VGA output increases contrast sporadically - ATI radeon x1400"
date: 2009-01-26
forum: Multimedia Software
---

### Post by konradpiskorz on 2009-01-26
The VGA output on my laptop, running an ati radeon x1400 video card and ati's proprietary drivers, for no deiscernable reason increases the contrast/brightness of the vga output every 5-10 minutes.

Every 5-10 minutes the brightness/contrast jumps up a 'step'.
Opening ati's catalyst control center resets the contrast to the original value and must be closed and opened again to reset the value again.

If this isnt done, the picture will slowly go from normal to an unreadable, unwatchable washed out picture.

I don't know if ati or xorg is malfunctioning.  Maybe my drivers aren't set up properly.

This is a pretty annoying problem as I really do not want to install windows just to be able to use my tv.

Could something be running that I don't know about every 5-10 minutes that causes this?  It never happens on my laptop monitor.  Could it be an error in ati's drivers?  Why does opening ati catalyst control center reset these values.  Why would they be increasing?  Why are video drivers so confusing in linux?

Sigh
Konrad

---

### Post by konradpiskorz on 2009-01-27
Added Info

Following this how-to to fix my sound : [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I noticed along the way that while installing something(dont know what)

```
fglrx: Multiple versions in DKMS. Unsure what to do. Resolve manually.
```

As far as I can tell DKMS stands for Dynamic Kernel Module Support.  So somethings up with my kernel perhaps?

---

### Post by konradpiskorz on 2009-01-27
Solved.

The problem dissapeared simultaneously when I got 1360x768 native resolution working on my TV by following this workaround.

[http://ubuntuforums.org/showthread.php?t=1051382](http://ubuntuforums.org/showthread.php?t=1051382)

Konrad

---


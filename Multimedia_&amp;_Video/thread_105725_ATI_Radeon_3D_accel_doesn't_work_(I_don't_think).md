---
title: "ATI Radeon 3D accel doesn't work (I don't think)"
date: 2005-12-19
forum: Multimedia &amp; Video
---

### Post by musther on 2005-12-19
Ok, I'll give you the background, and what I've tried.

I installed UT Game of the year ed, which ran well, so do GL screensavers, so I've always assumed that my 3D acceleration was working.  

I had UT 2004 installed in windows and it ran very well, so when I installed it on Breezy today, I was very suprised to find it jerky even with all the settings down  as far as they would go.  This got me thinking about whether my card was being used properly.

I ran glxinfo, which gave me (among other things) this output:

```
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
```

So I followed this howto:

[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

To install the fglxr driver, which went smoothly.  I modified my xorg.conf to tell it to use the "fglxr" driver rather than the "ati" one.  I restarted X, and everythig looked normal (apart from the fact that the position of the image on my screen changed, so I knew it was using a different driver).

I ran glxinfo, which gave me the same output as before, I also ran fglrxinfo which gave me the same basic info.

I tried to run glxgears, which worked but was very jerky (which it wasn't with the old driver), and then I tried both UT and UT 2004, both of which didn't even load.  

So, with the old driver, although GL seemed to work, I don't think it was using hardware acceleration, and with the new driver, although the driver itself seems to work, the 3D acceleration still isn't.

So, where do I go from here?

---

### Post by rachii on 2005-12-19
not sure if this will help out at all, but with breezy this howto is what worked for me
[http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")

---

### Post by musther on 2005-12-20
Thanks heaps, worked a treat....  I'm very happy killing people in UT2004 now!!!

---

### Post by rachii on 2005-12-20
glad i could bring such carnage to the world ;D

---


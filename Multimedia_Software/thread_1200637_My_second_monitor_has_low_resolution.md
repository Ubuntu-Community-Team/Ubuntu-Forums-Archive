---
title: "My second monitor has low resolution"
date: 2009-06-30
forum: Multimedia Software
---

### Post by alwayssummer on 2009-06-30
My second monitor should run at 1600x1200 (20" Dell) but the highest resolution the display dialog will give me is 1152x864.

Also, I can only drag windows into about 1/3 of the secondary display (the big monitor). 

I'm running a Dell Latitude D620. The graphics are on an embedded chip from Intel: 945GM Graphics Controller.

Also, lots of images (but not all of them) look funny on this OS, but not under Windows. For example, the smilies are all pixelated. 

Any ideas?

---

### Post by alwayssummer on 2009-07-01
At one point yesterday I had full use of both monitors (despite the second still being low-res). When I booted up this morning I can't even use all of my primary monitor.

I think this has something to do with the workspace size. I'll look into how to change the workspace size.

---

### Post by jimmux on 2009-07-03
I have the same issue. Similar resolution I'm trying to get, also on intel graphics. Using HDMI or VGA gets the same result. It would be nice just to get the correct aspect ratio, instead of all 3:4 options.

Let me know if you find anything, I'll see what I can discover as well.

---

### Post by jimmux on 2009-07-03
I found a solution... of sorts.

I kept running:

```
xrandr -q
```

to check available resolutions, while also opening display settings and setting the resolution to the highest available. After *some* restarts it would make higher resolutions available.

I had to repeat the cycle several times, each time getting a slightly higher resolution until I reached the maximum.

There was an issue where compiz would have problems if the secondary display was placed above or to the left of the primary. Weird, but in other positions it was fine.

---


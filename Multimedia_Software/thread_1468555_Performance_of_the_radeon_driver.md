---
title: "Performance of the radeon driver"
date: 2010-05-01
forum: Multimedia Software
---

### Post by Bellerophon on 2010-05-01
I've just jumped back into Ubuntu after last having an install of 8.10 for a while a bit back. Unfortunately, it seems that ATi is no longer supporting my laptop's X600 Mobility, and the legacy driver doesn't work on Lucid's version of XOrg, so I'm stuck with the open source radeon driver.

I was expecting reduced performance to be sure, but not to this degree. The computer can't even handle basic desktop effects; turning it onto 'normal' settings means that it jutters and lags a few seconds dragging windows around, freezes up as it fades a menu, stuff like that. I tried starting Tux Racer as a test and it just dropped resolution and then showed the top left corner of the entrance screen running at about a frame every two seconds. And the basic, few shapes pyOpenGL project I've been working on just segfaults when it tries to render something (as pyOpenGL is wont to do when it encounters a card that doesn't do something it wants to).

This isn't a powerhouse of a graphics card, but it's okay - over on Windows it can handle midrange 3D games like WoW, HoN, Portal, etc. Is such a massive loss of performance par for the course with the open driver, or is there something wrong with mine? I've tried switching it into Kernel Mode, to no avail.

---

### Post by Bellerophon on 2010-05-08
So I assume nobody has any legacy equipment here then.

---


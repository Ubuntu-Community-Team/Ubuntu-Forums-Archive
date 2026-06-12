---
title: "ATI HDMI output - cut off on all sides"
date: 2011-06-26
forum: Multimedia Software
---

### Post by telestrial on 2011-06-26
Hey,

Ubuntu 10.10

I'm using an ATI Mobility Radeon 3400 trying to do a multi-display desktop thing. The problem is that my TV is cutting off the picture on all 4 sides.  My resolution is set to 1600X900 on my laptop and 1360 X 768 (Preferred) for the DTV. I'm connecting via HDMI and it appears that in CCC it is recognized this way.

I read another post here on the forums that talked about overscanning being the issue..I see that option for the DTV HDMI monitor, but it is greyed out. Is this because I am using the preferred resolution? It just auto-magically configured it this way.

Any suggestions on how I can access the overscan slider and/or fix this issue?

Thanks!

---

### Post by 4Orbs on 2011-06-27
The problem might be that you need to open the CCC as root. In the terminal enter:
```
gksudo amdcccle
```
Then the overscan settings should be available.

---

### Post by telestrial on 2011-06-27
Thank you for your reply.  However, this is not the issue. I always run this program as root, and the option is still greyed out.  Any other suggestions? :)

---

### Post by 4Orbs on 2011-06-28
Well, now I discover that the new drivers... you don't need to open the CCC as admin, just as regular user. Have you tried that yet?

---


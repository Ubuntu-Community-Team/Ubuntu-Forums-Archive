---
title: "Mesa Drivers Question"
date: 2010-04-20
forum: Multimedia Software
---

### Post by X-Malleus on 2010-04-20
Hey everyone,

I just got done building the Mesa 3D drivers from source, and there's just one thing that I'm not sure about.  I noticed that the i810, i965, etc drivers in /usr/local/lib/dri/ were updated, but the DRI, DRI2, and GLX drivers in /usr/lib/xorg/modules/extensions were not.  Is this normal, or is there a step I missed?  My guess would be that these drivers would be updated for the entire Mesa to have been updated.

---

### Post by Yellow Pasque on 2010-04-20
If you didn't use --prefix=/usr with configure, then the files install to /usr/local/...

For an easier way, check out the xorg-edgers PPA, which is frequently updated.

---


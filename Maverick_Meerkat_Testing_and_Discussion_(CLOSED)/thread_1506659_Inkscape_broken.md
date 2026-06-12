---
title: "Inkscape broken"
date: 2010-06-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by eTM_ on 2010-06-10
currently scrolling in inkscape is broken. When a drawing scrolled parts of the image vanish and garbage occurs. its somehow related to gtk. Has anybody else this experience?

---

### Post by MacUntu on 2010-06-10
Another victim of enabling client-side-decorations. Try to start it from the command line with 'XLIB_SKIP_ARGB_VISUALS=1 inkscape'.

**Edit:**

I guess it's this one: [https://bugs.launchpad.net/ubuntu/+source/inkscape/+bug/586997](https://bugs.launchpad.net/ubuntu/+source/inkscape/+bug/586997)

---

### Post by ScislaC on 2010-06-10
That is indeed the one. Thanks for the tip on starting it btw. We hope to get Inkscape 0.48 out in about 3 weeks and it will hit the repos soon after. :)

---


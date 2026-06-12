---
title: "KDEnlive dependency problem."
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by Kumeelyun on 2007-10-24
I had tried installing KDENLIVE manually when I was in 7.04 with a mixture of debs from the Trevino repository and source. What I thought was .5 was .4 and so I took it out, or so I thought, and decided to wait when I found out that .5 would be available in the official repositories.

When I upgraded to Ubuntu Studio 7.10 I went straight for the KDENLIVE in Add/Remove. However, on installing it from add/remove I get this message:

```
E: /var/cache/apt/archives/libmlt-data_0.2.4-0ubuntu1_all.deb: trying to overwrite `/usr/share/mlt/modules/lumas/PAL/luma01.pgm', which is also in package mlt
```

Then I have to go to Synaptic which identifies libmlt as a broken package. When I mark it for removal, it removes kdenlive and libvalerie along with it.

I thought I could be rid of the message if I deleted the mlt folder in the usr/share directory but the error message still happens. I am trying to understand what is happening here and how I can correct it? Can anyone help me? I've posted in KDENLIVE's forum, but haven't had a response for days.

---


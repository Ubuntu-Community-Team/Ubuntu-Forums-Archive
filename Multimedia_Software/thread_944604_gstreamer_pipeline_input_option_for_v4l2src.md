---
title: "gstreamer pipeline input option for v4l2src"
date: 2008-10-11
forum: Multimedia Software
---

### Post by 0x656b694d on 2008-10-11
Hi,

How do i set the composite tv-tuner input as the default video input device?

Now it is set to "v4l2src device=/dev/video0", which is the tv-tuner, i need to specify the input=1. Is it possible?

Thanks!
-Mike

---

### Post by 0x656b694d on 2009-05-23
Ok, the solution that i use now is the dov4l utility. It switches current input of the tv-tuner card.
So if i wish to switch to s-video input, i do 'dov4l -t 1'. And then may turn back to television with 'dov4l -t 0'.

---


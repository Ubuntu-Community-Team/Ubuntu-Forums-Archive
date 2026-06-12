---
title: "Thin line around picture"
date: 2009-06-30
forum: Mythbuntu
---

### Post by laffinet on 2009-06-30
Hi!

I'm running 9.04 with an Asus M2N68-VM, using the onboard NVIDIA GeForce 7050PV+nForce 630a graphics card, connected to my LCD TV via HDMI.
There sometimes is an irretating line on one or more edges of the picture while watching liveTV, videos, recordings. It's sometimes green, sometimes white, can change while watching the same program. 

I remember something mentioned somewhere about "zooming" the picture by just a few pixels so that any artefacts will not be visible anymore. 

What do I need to do to achieve this ? Is it a xorg.conf setting ? If so, where and how ?

Thanks for any help.

---

### Post by laffinet on 2009-07-01
Bump.

Anyone ?

---

### Post by Jayy on 2009-07-02
Try setting the resolution (assuming you're doing 7020p) to 1280 x 720.

---

### Post by laffinet on 2009-07-02
I think I'm running at a higher resolution but will check that.

---

### Post by Jayy on 2009-07-02
If you set it to exactly 1280 x 720, which is the resolution of 720p, then there shouldn't be any left over screen space.

---

### Post by tgm4883 on 2009-07-02
There is a zooming in the playback settings that you can adjust for just a few pixels.  I can get a more definite location of it if you need it when I get home.

---

### Post by laffinet on 2009-07-05
Thanks, I found a setting in the playback section of the setup (TV settings). It's called vertical and horizontal scaling. Only problem is I can only apply one of the two, otherwise the picture becomes jittery (slight up and down jitter).
Just applying the horizontal scaling makes the whole thin look much better already, though, so I did that.

---


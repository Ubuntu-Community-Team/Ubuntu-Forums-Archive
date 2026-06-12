---
title: "Shrinked video with fglrx and tv out"
date: 2008-06-26
forum: Multimedia Software
---

### Post by fcmartins on 2008-06-26
Hello,

I'm using the fglrx driver for my ATI Xpress 200 onboard video card.

When I enable overlay video (sudo aticonfig --overlay-type=Xv) and tv out, any video content (DVDs, MPEGs, DIVXs and capture card videos) will display shrinked on my TV, the width will be ok, but the height (vertical) of the video will display shrinked by half.

The weird thing is that the rest of content, desktop, windows and console display perfectly, only the video shows "shrinked" on tv.

If I disable Xv overlay, it displays correctly in the TV. If instead of the TV, I use my regular CRT display and enable overlay, videos will display ok too.

I tested using the following programs: MythTV, TVTime and Totem.

---

### Post by fcmartins on 2008-06-27
I investigated a little more and I think my problem may be duo to the aspect ratio not being detected when I connect my TV. When using TV out, MythTV will print this:

> VideoOutputXv: Physical size of display unknown. Assuming 17" monitor with square pixels.

I'm using a regular CRT TV.

I also forget to note that, on TV, the shrinked video is displayed on the upper half of the screen, maybe this has something to do with interlacing or interleaving?

---

### Post by fcmartins on 2008-06-27
No one has any pointers on this?

---

### Post by fcmartins on 2008-07-01
Updated to the latest ATI drivers, 8.6, and everything is OK now.

---


---
title: "No video on second display"
date: 2006-09-02
forum: Multimedia &amp; Video
---

### Post by janbanan on 2006-09-02
Hi,

I've a problem that I can't solve. I'm using dual monitors. First my TFT-screen and the second is my TV-screen. It's a clone screen and it works fine untill I wan't to see a video-file on my second screen(TV). The video-file works fine on the TFT but there is no picture on my TV, It's just black. Sound works tough. Second problem is the resolution on my second screen(TV) I think becouse it does not fit(to big) for my TV.

---

### Post by Nicksha on 2006-09-02
You have to change the resolution to no more than 1024x768, so you wouldn't have the picture that doesn't fit on the tv.

Then, you have to put the overlay on the tv, by typing this in the terminal:

aticonfig --overlay-on=1

Later, to return it to the monitor, type:

aticonfig --overlay-on=0

---


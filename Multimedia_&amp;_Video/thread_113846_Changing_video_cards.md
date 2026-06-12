---
title: "Changing video cards"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by vanhonk on 2006-01-07
I'm going to be changing video cards soon and I could use a heads up on any roadblocks I might encounter.


I currently have a GeForce4 MX 440 that is working fine. I am also using a 19 inch flat panel which works great as well.

I just ordered a GeForce 6200-A with dual monitor support and another 19 inch flat panel. My plan is to remove the old card, and install the new card with dual monitors. Doing this in windows for me would be an easy task, but I am new to Linux and Ubuntu "love it!" and I am looking to learn something new.

Thanks ;)

Oh yeah, I have no idea how to begin

---

### Post by taurus on 2006-01-07
You have to configure /etc/X11/xorg.conf again.  You can do that with

sudo dpkg-reconfigure xserver-xorg

---

### Post by mo_x on 2006-01-07
You have to look into setting up TwinView or multiple X screens. Check out the readme that comes with the nvidia drivers. There are also some threads on this forum. And there is always google :)

---


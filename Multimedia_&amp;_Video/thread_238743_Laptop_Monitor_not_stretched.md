---
title: "Laptop Monitor not stretched"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by pteri498 on 2006-08-18
I'm trying out the Ubuntu live CD. When I start it, I find that my monitor screen size is too small to fill the screen when it's anwhere below 1280x1024. It appears that Windows XP does the stretching itself. I remember when installing XP, before I installed the specific video drivers the same problem occurred there.

I had this same problem using Knoppix. I somehow fixed this with framebuffer switches or nodds or something, but I've tried several times recently and that same fix doesn't do it.

Does anyone know what I can do to get the screen to stretch at any resolution?

Here is my computer information:
Brand: Compaq Presario 2500
Video: ATI Radeon IGP 345M

---

### Post by bigken on 2006-08-18
in a terminal type dpkg-reconfigure xserver-xorg and use the space bar to select your screen sizes ;)

---


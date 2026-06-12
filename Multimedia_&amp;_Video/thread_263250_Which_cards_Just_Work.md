---
title: "Which cards Just Work?"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by podunk on 2006-09-22
Is there a video card that will "Just Work"? One that will run Open GL and with 3D acceleration that there are drivers for that won't get broke every time a patch comes out?

I'm no where near being ready to start compiling my own kernels or anything like that.

I have an ATI Radeon 9200 SE and it doesn't work very well at all for games. glxgears runs just over 100 FPS. :-)

I want to play some games and install compiz and I will need a new card it looks like. Is there a spec somewhere or a guide as to which cards actually work?

When I install the new card, will I need to completely redo my Ubuuntu?

Thanks in advance!

---

### Post by goatflyer on 2006-09-22
You might find this list helpful:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)


I'm using the nVidea GForce4 MX 460, I had to read a lot of howtos, etc. to get (in order) 3D acceleration, GLX, Compiz.  glxgears in compiz gives me about 3000 FPS.

You wont have to recompile any kernels when you change video cards, but you might need to do anything from reconfiguring your xorg.conf as a minimum, to reinstalling ubuntu as a maximum.

Not being an experienced Linux techie, I'd back up your /home partition and then reinstall Ubuntu --- its quicker!!!

---

### Post by podunk on 2006-09-23
Hey thanks!

Funny thing is - it says my card should work?

And I agree about starting over often being the best way to "fix" stuff. :-)

---

### Post by m.musashi on 2006-09-23
> **podunk said:**
> Is there a video card that will "Just Work"? One that will run Open GL and with 3D acceleration that there are drivers for that won't get broke every time a patch comes out?

I'm no where near being ready to start compiling my own kernels or anything like that.

I have an ATI Radeon 9200 SE and it doesn't work very well at all for games. glxgears runs just over 100 FPS. :-)

I want to play some games and install compiz and I will need a new card it looks like. Is there a spec somewhere or a guide as to which cards actually work?

When I install the new card, will I need to completely redo my Ubuuntu?

Thanks in advance!
I just installed an XFX 7600 GS and it is working without a hitch. I had installed the nvidia drivers with automatix and I think it is either the same driver for this card or the update it just did installed the right driver. In any case, it is working fine. Glxgears at 5500 fps or so. Is that good? I'm not a gamer so I got the one with the passive cooling. I have been playing planet penguin and neverball. Everything in very smooth.

I didn't have to do anything to my dapper install. It did run an update when I logged in but it may have been ready for one anyway - I don't know. I didn't see the 7600 GS on that list but it's working fine. It's $115 at Tigerdirect and Newegg. Not the best card out there but then it's not the most expensive either. And it's very quiet. Good luck.

EDIT: Oh, and the install was easier than in Windows. I did uninstall the windows drivers first and when I booted I got a black screen. Ubuntu, however, booted without any problems and worked immediately. I love Ubuntu.

---


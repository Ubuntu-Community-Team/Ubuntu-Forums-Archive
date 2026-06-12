---
title: "Can't play videos, only getting sound with A31G motherboard"
date: 2010-08-06
forum: Multimedia Software
---

### Post by GeoMX on 2010-08-06
I'm testing a rather old motherboard (PC-Chips A31G) with both Ubutu Karmic and Lucid, everything seems to work fine but video playing.

I tried flv, mp4 and mpg with both mplayer and totem, but I can only get sound with no video, well, not a black screen but a deformed image (I don't attach an image because every attempt to capture the screen gets a black or transparent video).

I already installed ubuntu-restricted-extras package witho no luck.

What I don't understand is that, if I switch to another motherboard (using the same HDD), everything works perfect. I guess it's a problem with the motherboard's video chipset, but would like to confirm this and know whether there is a solution.

I attach lspci output for the A31G motherboard.

Thanks in advance for your help.

---

### Post by ajgreeny on 2010-08-06
I think it is you SiS video card that is the problem so do a good search of google with the terms **SiS 661/741/760 PCI/AGP ubuntu** or better go to [http://www.googlubuntu.com](http://www.googlubuntu.com) and search there.  It's a sort of dedicated ubuntu google system that I use a lot.

---

### Post by GeoMX on 2010-08-06
Yes, the problem is the SiS card, I have already searched the web and the only option I found was setting kaffeine to use the xshm driver, but it didn't work for me (I tried mplayer and totem). However, I tried x11 for mplayer and now I can watch videos, guess I should forget about something more demanding with this board.

Thanks for your reply.
-----------------------------
Update: I can play videos, but while watching them, system halts every now and then, I have no clue what is causing it since I can't find any related log message.

---


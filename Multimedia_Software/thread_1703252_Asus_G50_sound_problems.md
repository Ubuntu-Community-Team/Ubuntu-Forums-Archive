---
title: "Asus G50 sound problems"
date: 2011-03-09
forum: Multimedia Software
---

### Post by yax51 on 2011-03-09
Hello I was having issues with my sound on my Asus G50VT, and I searched for hours to get everything working properly, the headphones, speakers, mic, ect. But I finally found a solution that was REALLY easy, almost stupid really.

I added the line:

options snd-hda-intel model=asus-mode3

to the end of /etc/modprobe.d/alsa-base.conf

So here is a short walkthrough for beginners:

Open the Terminal: Applications > Accessories > terminal

type in, or copy and paste, this:

gksudo gedit /etc/modprobe.d/alsa-base.conf

Then at the very end of that file paste:

options snd-hda-intel model=asus-mode3

Save and reboot.

Now your sound should be working perfectly!!!

:D:D:D

---


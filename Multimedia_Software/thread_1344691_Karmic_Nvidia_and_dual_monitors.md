---
title: "Karmic: Nvidia and dual monitors"
date: 2009-12-03
forum: Multimedia Software
---

### Post by Justin C. on 2009-12-03
I've been having a really rough time getting my second monitor to work. In 9.04, I just plugged it in and it allowed me to use it as a second monitor (i.e. my whole desktop was contained on my laptop, and the second monitor was there to drag things to). Now, the nvidia tool only allows twinview and separate x screen. Twinview stretches my desktop across both monitors. Is there a way to set up my second monitor as a second space for dragging and dropping windows?

Thanks,

-Justin

---

### Post by gradinaruvasile on 2009-12-03
What options did you have in 9.04? Separate X screen?

---

### Post by gradinaruvasile on 2009-12-03
I have all 3 options (drivers version 195.22) available: TwinView, Separate X screen and disabled.

What hardware and driver version do you have? (lspci)

Was there another option in 9.04 beside these?

---

### Post by Justin C. on 2009-12-03
I had the same options in 9.04, but TwinView made the second monitor more like a second workspace if I remember correctly. I have a Dell Vostro 1400. The second monitor is an LG HDTV. My Nvidia driver is 173.14.20. Maybe that's the problem? My graphics card is an 8400 GeForceM. Thanks for your help!

---

### Post by wojox on 2009-12-03
Just reboot and the stretch will go away.

---

### Post by doas777 on 2009-12-03
well, there are only the two options, either twinview or xscreens (has been that way since I started with Feisty). there also used to be xinerama, but it has been obsoleted by xrandr and twinview (and it was a finicky beast at that).

seperate xscreens works well, as long as you do not need to drag application windows from screen to screen. if you do, then Twinview is the way to go, but the configuration may not like being switched from single to dual head on the fly. never tried it.

also, i don't know about the 'M' line, but I've had some bad luck with Geforce 83/8400 cards before. bad tv overscan (or underscan to be more precise), and a lack of driver features.

---

### Post by Justin C. on 2009-12-07
Thanks guys. 

I ended up finding instructions on updating my nvidia proprietary driver from the terminal, and then twinview worked as it used to on 9.04.

---


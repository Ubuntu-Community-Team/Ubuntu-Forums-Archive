---
title: "Psychedelic Colors in X with GeForce 3 - unusable graphics"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by flah11 on 2007-02-03
I am running Ubuntu 6.10 and have a GeForce 3 nvidia card installed. No problems for several months. After a recent (too hasty) click to update, I lost X and was unable to recover from this - "No Screens etc.". I decided to use 'envy' which seemed to install the latest compatible nvidia driver.

Although it loads ok, the colors are all wrong, including the standard icons, and usually of a garish or psychedelic nature. Any graphics displayed is weird and effectively makes the pc unusable for anything other than text (See dump of desktop - had to reduce in size but you can see the effect). I have looked at the settings in 'nvidia X-server settings' but cannot fix the problem.

The unusual colors can be seen at the login screen, as soon as X loads, and I have tried changing a few xorg.conf settings, but don't really know which ones to alter, but have had no success. Scouring forums, I cannot find anyone else with this problem.

---

### Post by faferreyra on 2007-02-12
According to [this message]("http://www.nvnews.net/vbulletin/showthread.php?t=77816") on the NVIDIA forums, it happens when you use the DVI output on the card. It's a bug on the driver, and still there's not a fix. If you can, and you want, use the Analog output. I'll try it right now, I'm having the same problem.

---


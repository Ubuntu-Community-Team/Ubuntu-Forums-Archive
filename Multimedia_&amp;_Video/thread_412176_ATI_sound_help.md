---
title: "ATI sound help"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by hacc on 2007-04-17
Trying to get my sound card working in ubuntu edgy 6.10 and i noticed the alsa-conf util is missing, is there a way to install the sound driver without alsa-conf that anybody knows of? Here is the output of lspci for my audio card if anybody knows how to install it directly. 00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)

thnx,
hacc

---

### Post by kornhead127 on 2007-04-17
What motherboard do you have, I'm guessing it is an internal soundcard.

---

### Post by hacc on 2007-04-17
btw its built in and its a gatway LAPTOP model:6453

---

### Post by kornhead127 on 2007-04-17
Your sound card is a SigmaTel, It says ATi because of the Ati Xpress 1150 chipset. Which means it should be supported with alsa. try to update alsa-base.

---

### Post by hacc on 2007-04-17
first, i did update the alsa-base and second i can not find alsaconf, is there a replacement

---

### Post by kornhead127 on 2007-04-17
You can try alsa-tools-gui or gnome-alsamixer.

---


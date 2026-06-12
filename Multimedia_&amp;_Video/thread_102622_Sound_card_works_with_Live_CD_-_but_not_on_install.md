---
title: "Sound card works with Live CD - but not on installation"
date: 2005-12-12
forum: Multimedia &amp; Video
---

### Post by northie on 2005-12-12
Hey. 

After a few sound card switches, my sb live! won't work within my main drive ubuntu, but springs to life at a Live CD boot. Can I reset my hardware detection, or whatever I now have to do, without reinstalling the OS?

lspci detects the card without problems, but my gnome volume controller has a red x next to it, and the "default sound card" box under system/preferences/sound is clean empty. aplay -l gives: "aplay: device_list:218: no soundcards found..."

Cheers,

- northie

---

### Post by northie on 2005-12-12
Solved this with the inexhaustible help of crimsun in #ubuntu.
I'd messed up some drivers well and good, and had to reinstall my kernel with "sudo apt-get --reinstall install linux-image-$(uname -r)", whereupon I could load the driver with "sudo modprobe emu10k1"

---


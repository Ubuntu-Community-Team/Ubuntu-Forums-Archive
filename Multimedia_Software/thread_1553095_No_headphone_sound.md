---
title: "No headphone sound"
date: 2010-08-14
forum: Multimedia Software
---

### Post by jandugacek on 2010-08-14
I have a problem with headphone sound with my Ubuntu 10.04 on laptop Acer Aspire TimelineX 4820 TG. When I insert the headphones, the sound from speakers stop, but there is no sound in the headphones. Manipulating with the alsamixer did not help. Modifying /etc/modprobe.d/alsa-base.conf also did not help. Can someone help me?

---

### Post by jandugacek on 2010-09-12
The problem was not in alsamixer, but in kernel and bios. Linux headers 2,6-35-7-generic solved this problem with many other problems of this notebook (no battery status indicator, unability to change graphic card).

---


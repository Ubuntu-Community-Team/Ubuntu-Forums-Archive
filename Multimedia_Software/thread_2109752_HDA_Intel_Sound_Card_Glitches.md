---
title: "HDA Intel Sound Card Glitches"
date: 2013-01-28
forum: Multimedia Software
---

### Post by crazyjay118 on 2013-01-28
Hi. I've been using Ubuntu for a little while now, and one problem that has always annoyed me is random glitches in sound output. This usually consists of random clicking and/or small parts of sound being missing/played twice etc. I'm reasonably sure this is due to Pulse Audio as it is independant of what application I am using (including Audacious, Firefox and VLC).

Furthermore, if I use DeadBeef to send sounds directly to ALSA (presumably bypassing Pulse Audio) these problems are eliminated, though this only works for Deadbeef and is not ideal as it comes with its own problems - namely having to click play multiple times before anything plays and if I try and play any other sounds from say Firefox, no sound will be output and Firefox will crash (I presume this is because Deadbeef has taken complete control of ALSA).

I've done some googling on common Pulse Audio problems and tried changing various configuration items:

[LIST]
[*]setting tsched = 0 made the problem worse
[*]raising the priority, disenabling cpu limit and adjusting buffer fragments sizes didn't help noticeaby
[/LIST]
So my question is, is there a way to fix Pulse Audio for lower-spec laptops using on-board HDA Intel chips, or otherwise is there an alternative such as sending everything to ALSA directly?


Technical info: Ubuntu 12.10 (had same problem in 12.04 before updating in the hope of fixing it) on Toshiba Satellite C660-125 w/ dual core Intel Celeron 2.1GHz, 3GB RAM and Intel HDA sound.

---


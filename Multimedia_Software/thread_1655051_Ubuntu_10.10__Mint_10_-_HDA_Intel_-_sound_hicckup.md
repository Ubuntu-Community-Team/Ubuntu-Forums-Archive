---
title: "Ubuntu 10.10 / Mint 10 - HDA Intel - sound hicckup"
date: 2010-12-29
forum: Multimedia Software
---

### Post by Qdlaty on 2010-12-29
Hello,

on my GF's laptop after upgrading from 9.04 during playing music (radio stream or mp3) from time to time we have distortion like a one second loop of played music.

First I thought that's pulseaudio problem so I have removed it from the system. No change.
Also changing kernels did not help. 2.6.35, 2.6.36, 2.6.37 - all the same.

I did try to recompile alsa using AlsaUpgrade script but it is either failing to compile or (with snapshot option) kernel cannot load new modules.

The alsa info can be found here:
[http://www.alsa-project.org/db/?f=f56b2c84f894aeb75d1a1d93b923f4e70c7b5ec6]("http://www.alsa-project.org/db/?f=f56b2c84f894aeb75d1a1d93b923f4e70c7b5ec6")

I did also noticed the kernel messages of:
**CE: hpet increased min_delta_ns**
and
**hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.**
but I have no clue how to deal with the problem.

I'm running out of time. Either I'll spent New Year's day on reinstalling the 9.04 or she will have to live with crappy sound for next two months before I'm back home again.

---

### Post by Qdlaty on 2010-12-29
To bump my thread (:D) I can add that with kernel 2.6.33-realtime I've even more sound loops while keeping the mouse over a window button or not moving it at all. If I start to move the pointer sound loops disappear.

Unfortunately I cannot run 2.6.37-lowlatency kernel due the fact it is not running with nvidia (black screen).

---

### Post by Qdlaty on 2011-01-01
One more observation - the sound loops can be triggered when leaving the mouse without any move. If mouse is moving - music is unlocked.

---

### Post by miketyson986 on 2011-01-20
hi, i like that..thanks.

---


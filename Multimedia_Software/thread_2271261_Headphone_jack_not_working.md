---
title: "Headphone jack not working"
date: 2015-03-28
forum: Multimedia Software
---

### Post by luca36 on 2015-03-28
Hello,

I'm running Ubuntu 14.0.4 x64, with an Asus X99-A motherboard.

Recently, my audio jack stopped working. going into the pulse audio control, I still see activity on the slider for the device when playing sounds, but nothing comes out of my headphones. Other audio outputs (such as the nvidia HDMI one) work.

Here's the result to an alsa info script:

[http://www.alsa-project.org/db/?f=cbf7f29bea0193312062aa9e8184a36075375059](http://www.alsa-project.org/db/?f=cbf7f29bea0193312062aa9e8184a36075375059)

---

### Post by Oliver_Evans on 2015-03-28
I'm no expert, but here's my two cents.

When I launch ```
alsamixer
``` [(Picture)]("http://imgur.com/EgCJ9Ns") 

there are individual volume controls for headphone and speaker, sometimes I'll find that one of them was muted.

Hopefully it's that simple!

---

### Post by luca36 on 2015-03-28
Nope, none of them are muted.

---


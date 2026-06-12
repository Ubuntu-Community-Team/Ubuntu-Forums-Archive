---
title: "Problems getting Phonon sound via HDMI"
date: 2011-07-30
forum: Multimedia Software
---

### Post by reddish on 2011-07-30
Hi, I am using Ubuntu 11.04 64-bit on an Intel H67-based motherboard that supports on-board A/V, and sports HDMI output. I am trying to get audio over HDMI.

Using ALSA, this works fine, outputting crisp audio via HDMI:

aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav

However, Phonon (with its standard 'gstreamer' back-end) doesn't appear to find the device.

What would be the next step to solve this?

---


---
title: "How to install missing wine ALSA driver in ubuntu"
date: 2010-08-06
forum: Multimedia Software
---

### Post by opengl_cpp on 2010-08-06
Whenever I try to run a windows game under Wine I get an error that depict I have no proper sound driver. I checked the wine config and there was only OSS option that I think it would not help me to get sound working. I think I have to use Alsa Instead but I don't know how to add Alsa support to wine.
By the way in need DirectSound as well. should i download it myself and add it to system32 or there is a better way?
I use:
ubuntu (Meerkat) 10.10
wine 1.2

---

### Post by Yellow Pasque on 2010-08-06
Can you run winecfg in a terminal and click on the audio tab? Generally, the ALSA driver should work without issue. If you're running 64-bit Ubuntu, you need ia32-libs package, or more specifically, lib32asound and lib32asound-plugins packages.

---


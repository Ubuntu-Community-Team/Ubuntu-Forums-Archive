---
title: "Chrome 	96.0.4664.45  - unable to force YT to use HW decoder"
date: 2021-12-03
forum: Multimedia Software
---

### Post by a1-andrzej on 2021-12-03
I'm using 9700t with iGPU
i have tried to add below flags, with non free intel drives installed:

--use-gl=desktop --enable-features=VaapiVideoDecoder --use-gl=desktop --ignore-gpu-blocklist --enable-gpu-rasterization --enable-zero-copy

in chrome:gpu i see, hw support  is enabled, but when checking YT videos are still played using: VpxVideoDecoder and Hardware Decoder is set to :false


Any suggestions?

---

### Post by monkeybrain20122 on 2021-12-06
What format is the YT stream in question? It won't work if stream is in av1 (may or may not work with vp9, hardware decoding works with Nvidia 470, not sure about intel) Vappi does work on my old toshiba labtop with intel graphic but I use h264ify so stream only in h264 (so no higher resolution than 1080p)

BTW you didn't say which Ubuntu version is that. Are you on Wayland or Xorg?

---

### Post by bomc68000 on 2021-12-17
I have other hardware platform (AMD), but first of all verify if VAAPI works actually (by means of 'vainfo' or even better in a media player that can take advantage of HW acceleration).
As someone pointed out, only selected formats may be actually supported. In my case it's practically only H264 and the only solution was to install Chrome extension called "h264ify" which does the job of ensuring the H264 format is selected (if available of course).

---


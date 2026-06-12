---
title: "Mic poor quality"
date: 2018-12-23
forum: Multimedia Software
---

### Post by startni on 2018-12-23
Hey,

My mic is a bad quality on Ubuntu 18.04.1 LTS. I have the drivers installed however it still sounds poor.

It sounds perfectly fine on Windows 10, so I don't understand why it's bad on Ubuntu. 

Here are my drivers:
[IMG]https://i.imgur.com/Pyfqwqc.png[/IMG]

My headset is a Razer Kraken Pro V2.

Hopefully I can get this fixed quick :/

---

### Post by wildmanne39 on 2018-12-23
*Thread moved to **Multimedia Software for a more appropriate fit**.*

---

### Post by CatKiller on 2018-12-23
You haven't described the nature of the "poor quality." I suspect you've just got it turned up too high, so it's clipping.

---

### Post by startni on 2018-12-24
There's a lot of static in the background, I tried turning the Capture devices up and down and changing them in alsamixer however no luck.

---

### Post by startni on 2018-12-24
bump

---

### Post by CatKiller on 2018-12-24
> **startni said:**
> There's a lot of static in the background, I tried turning the Capture devices up and down and changing them in alsamixer however no luck.

Have a look in alsamixer for a mic pre-amp setting. It might be called Boost or similar, and it could be a fader or a toggle. Try turning that off. Also try muting any inputs you aren't using. 

I also found [this post](https://bbs.archlinux.org/viewtopic.php?id=210840) with seemingly similar symptoms to yours. They fixed it by adding ```
options snd-hda-intel model=generic
``` to their /etc/modprobe.d/sound.conf.

---

### Post by vandmed on 2018-12-27
How can I improve the mike quality?

---


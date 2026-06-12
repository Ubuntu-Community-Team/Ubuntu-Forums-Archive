---
title: "Leadtek WinFast DTV Dongle H Plus in Ubuntu 12.04"
date: 2012-08-14
forum: Multimedia Software
---

### Post by borivoje on 2012-08-14
I have just bought the above Tuner dongle and can't set it up under latest Ubuntu. All packages that I have tried to compile ( [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)) are for 2.6 kernels and report errors while compiling. I have currently on my machine 3.5 Ubuntu kernel which has modules for this card. They are dvb-usb-dba0700, which load after modprobe, but don't create any interface for application access. Is there any solution for this, or did I make poor choice.

---

### Post by lukeiamyourfather on 2012-08-14
You should see a /dev/video* for each tuner. It might be worth trying on an older release like 10.04 LTS which still supports the 2.6 kernel.

---

### Post by borivoje on 2012-08-14
Thank you lukeiamyourfather for the quick reply!

I'm considering this option as the last resort, since I have some devices which do not support older kernel.

From what I have read so far, it seems that chips that run this dongle are rather old, meaning that some support might have been provided so far. 

I didn't mention that I need analog support for this card, nameley PAL-BG or something, which is the standard here in my country.

Still holding on...

---

### Post by borivoje on 2012-08-14
Just one more quick hint, regarding the previous post. I have in my dev /dev/video0 which is my laptop webcam

---


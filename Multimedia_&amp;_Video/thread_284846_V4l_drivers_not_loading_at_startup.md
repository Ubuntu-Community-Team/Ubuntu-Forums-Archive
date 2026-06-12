---
title: "V4l drivers not loading at startup"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by elbeasto on 2006-10-26
Hi,
I finnaly managed to get my Dvico Fusion HDTV Hybrid up and running using the v4l drivers. I found that Kaffeine was the only program that worked with digital (haven't tried mythtv yet). Kdetv, tvtime and xawtv work with analog but with no sound.

The problem is that every time I reboot I have to go to the v4l-dvb directory and type:

```
sudo make reload
```
before Kaffeine will have the dvb button enabled.

How do I get these drivers to load at startup?

Thanks

---

### Post by magicfab on 2006-10-27
Normally you would add the driver to /etc/modules . What does lsmod return ?

---

### Post by elbeasto on 2006-10-27
I installed 6.10 this morning and it seems to work fine now :) 

Thanks for the reply tho.

Steve

---


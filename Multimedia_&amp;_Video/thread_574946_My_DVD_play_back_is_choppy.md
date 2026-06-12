---
title: "My DVD play back is choppy"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by carlinuxlearner on 2007-10-13
I've have been doing some research, I believe I have all the right codecs, so I think it's some DMA problem. I tried enabling DMA but this is what I got.
"carl@carlubuntu1:~$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
carl@carlubuntu1:~$ "
I have no idea what to do, please help me.

C@RL

---

### Post by linuxwizard on 2007-10-13
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

Also do you have any desktop effects enabled ? If so try disabling them than try a DVD and see if that helps.

---

### Post by carlinuxlearner on 2007-10-13
Yes I (had) compiz-fusion running, I stopped it, but it's still not up to quality, it's a little jerky, here's my computer stats 1.3GHz Intel celeron CPU, 256MB RAM, Nvidia Geforce4 MX 420, On board intel graphics chip (no in use). I know it can do it because I had kubuntu 7.04 installed and it worked just fine, but after installing Ubuntu 7.10 it's not, working right. Any other suggestions?

C@RL

---

### Post by linuxwizard on 2007-10-13
Did you check to make sure you have enable DMA transfer ? Which player are you using if Totem I have seen a few posts about issues with it.

---

### Post by carlinuxlearner on 2007-10-13
See first post. And I'm using Kaffeine, and VLC, both do the same thing.

C@RL

---

### Post by shomati_sen on 2007-10-15
I have the same problem. Typing "hdparm -d1 /dev/scd0" or "hdparm -d1 /dev/cdrom" doesn't work. I get the same error as listed above. There is no /dev/hdc. 

Shomati

---


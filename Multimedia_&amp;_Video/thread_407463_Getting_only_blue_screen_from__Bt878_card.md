---
title: "Getting only blue screen from  Bt878 card"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by jazzgossen on 2007-04-12
I'm trying to get my TV card working under Ubuntu. I've connceted the aerial cable, but all I see from /dev/video0 is a blue screen with some static in it, as if there are no channels.

 I've tried both xawtv and mythtv. Running scantv finds no channels, but when I connect my digial camera to the composite input of the TV card and pick "composite" from xawtv's menu instead of "television", I see the images sent by the camera, although only in black and white. Any ideas of what to do? I'm running Dapper here. Below is the relevant output from lspci -v
```

lspci -v

0000:01:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at d4000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at d4001000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>

```

---

### Post by jazzgossen on 2007-04-12
I solved the immediate problem myself. Apparently the TV card wasn't autodetected properly. Looking at [this list]("http://linuxtv.org/v4lwiki/index.php/Cardlist.BTTV"), I saw that I need to specify card=100 for my card.

What I did, for future reference:

modprobe -r bt878 (because the bttv module was used by that module)
modprobe -r bttv
modprobe bttv card=100

Now I can watch TV in xawtv. I just need to find a way to get anything but static in mythtv and also find out how to set the card=100 option automatically at boot.

---

### Post by cylon359 on 2007-04-13
You should be able to put a line "options bttv card=100" in /etc/modprobe.d/options

---


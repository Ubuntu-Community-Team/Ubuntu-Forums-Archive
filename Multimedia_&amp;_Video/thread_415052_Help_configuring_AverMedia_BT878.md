---
title: "Help configuring AverMedia BT878"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by tamray on 2007-04-20
Is there a tool that will help me set the parameters on my AverMedia TV tuner, video capture card? I am trying to capture video via the composite port via VLC. I have changed the input channel from 0, to 1, but that has not helped. On my windows box, I had an app that configured things, so the encoder would receive the proper video source.

I am running Ubuntu 6.10


lspci and lsmod show the following:

00:0e.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:0e.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)


tuner 54828 0
tvaudio 26012 0
bttv 176116 2 bt878
video_buf 27652 1 bttv
ir_common 28548 1 bttv
compat_ioctl32 2432 1 bttv
i2c_algo_bit 10376 1 bttv
i2c_viapro 9876 0
v4l2_common 17280 2 tuner,bttv
btcx_risc 6280 1 bttv
tveeprom 16144 1 bttv
videodev 10752 2 bttv
i2c_core 23424 7 i2c_ec,tuner,tvaudio,bttv,i2c_algo_bit,i2c_viapro,tveeprom

---

### Post by cleverlyinsane on 2007-08-26
just wondering if you ever got your card working, i have the same card, and having problems, can't get ti to work properly.

Dan

---

### Post by zhinker on 2007-08-28
It wont work, no one's bothered to write a driver for it yet.  I've just resigned myself to finding another card and switching to XP for tv in the meantime

---

### Post by ontik on 2007-08-31
I'm pretty sure I have the same card.  I was running _K_ubuntu until a few days ago but when I was I had it working.  The way I did it was to inspect the card and I got some model number off a sticker on the card itself.  I googled that and 'kubuntu' and quickly found a solution.  I should have written that number down cos I've just installed Ubuntu (cos I reckon the docco is easy few a noob nuffy such as myself) and now have to do it all over again.

But I did get it working fine.  If I remember I'll post up my results.


ontiK.

---


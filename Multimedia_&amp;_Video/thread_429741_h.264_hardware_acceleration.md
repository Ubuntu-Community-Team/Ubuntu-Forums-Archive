---
title: "h.264 hardware acceleration"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by finite9 on 2007-05-01
I have an HP dv9297ea laptop with a GeForce Go 7600 which has hardware acceleration for H.264.  I am using Feisty with nvidia-glx drivers 96.31 but when viewing a h.264/aac tv rip in Totem, it jerks along quite badly.  Xvids/DVDs etc play fine.

I am assuming that this is because the driver and or totem are not using the hardware acceleration.  So my question is, 

Does the 96.31 linux driver support h264 hardware accel.?
How do i check if it does or doesn't?
Does or can Totem take advantage of the driver acceleration, ie, does support for this need to be baked into the player application as well?

---

### Post by Cappy on 2007-05-04
*bump* I have this same problem! The codec shows up as: "H264" when I click on the file's properties. The playback is perfect when the codec is "H.264 / AVC" or "ITU H.264". The format container for "H264" is a MKV but all other codecs in the MKV container work perfectly. I'm using a Geforce 7900GS. I had this problem on my 32-bit OS too (ATI 9800 Pro) but I didn't care too much because it worked with VNC. However, now when I play these videos in VNC on my 64-bit Feisty I get random crashes while I'm watching .. not fun.  I have a lot of these H264 videos from various places so it isn't that the video is corrupt.

Edit:
I opened these videos in MPlayer and the videos work perfectly (no lag at all!) if I use the "gl" driver on the video tab. I tried every other driver but they didn't work as well. gl2 and xv ALMOST work but it's still a little "laggy".

---


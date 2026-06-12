---
title: "nvidia 8500 8600 for decoding x264 h264"
date: 2008-07-11
forum: Multimedia Software
---

### Post by onesojourner on 2008-07-11
I am looking into upgrading my media center. I need to be able to play 720p and 1080p videos in x264 .mkv format. I will be using ubuntu or ubuntu server with xbmc. I have read that the nvidia 8500/8600 cards have the ability to decode h.264 videos. is this true with the ubuntu drivers or is this a vista only feature? and does it apply to .mkv files? I need to keep this under $200 if possible. I need a to upgrade the mother board (has to have at least 4 sata ports and room for a dolby capible sound card down the road), cpu and video card.

---

### Post by wolfen69 on 2008-07-11
if you get the proper video card, you should have no problems decoding. [here]("http://packages.ubuntu.com/hardy/graphics/x264") is the package for H264 playback. it is also available in synaptic.

---

### Post by bedahr on 2008-07-21
Hi onesojourner!

If you mean the Purevideo-functionality I am afraid this is not possible with the Linux-drivers.

The only accelerated playback possible is per xvmc which only works with mpeg2 files (and even there you can't use any advanced deinterlacing etc.).

ATIs Avivo isn't supported by there Linux-drivers either, btw (and as XVideo is not available in the HD* cards you'll be even worse off until _some_ kind of acceleration at least for video-display is implemented).

Given a decent CPU, 720p material will decode fine (I had only one (h264) 720p file which I would get choppy plaback on: 30fps and very high bitrates).
1080p is a bit harder to decode and at least my c2d 6300 can't do it (_very_ low fps in high-bitrate scenes).

There has been some success on getting CoreAVC running on Linux, tough.
It is messy and non-free software but it is fairly cheap (~15$) and very fast.
1080p playback on slightly older hardware should not be a problem with CoreAVC.

My personal hope is that the ffh264 decoder will get support for N-core-decoding which would allow smooth playback of 1080p media on nearly any dual-core. As I understand it, this is, however, a fairly complicated process because the h.264 codec is very complicated itself. (translation: this could take a while :))

Good luck!

-- bedahr

---

### Post by onesojourner on 2008-07-22
Thanks I did get a response back from nvidia. They confimed what you said. Hopefully we will get support for this kind of thing soon. It is a shame to have to spend $200 on a processor just to play some video files.

---

### Post by Duranxl on 2008-09-24
Any news on this?
I really want 1080p on ubuntu (i'm on 8600M GT)

---

### Post by onesojourner on 2008-09-24
contact nvidia, tell them you want support for this in the linux drivers. Thats the only way its going to change.

---

### Post by Duranxl on 2008-09-29
> **onesojourner said:**
> contact nvidia, tell them you want support for this in the linux drivers. Thats the only way its going to change.

So you believe that they are like "naaah, those linux people don't want HD support in our nvidia drivers"

?
:???:

---

### Post by onesojourner on 2008-10-09
Yep thats exactly what I am saying. Until we make a big fuss companies don't give us what we need/want.

---

### Post by Duranxl on 2008-10-09
> **onesojourner said:**
> Yep thats exactly what I am saying. Until we make a big fuss companies don't give us what we need/want.
well then why did they make linux drivers in the first place

---

### Post by onesojourner on 2008-10-11
we made a big fuss.

---

### Post by bedahr on 2008-10-13
> Until we make a big fuss companies don't give us what we need/want.
< well then why did they make linux drivers in the first place 
> we made a big fuss. 

This made me smile :)

Sadly I don't think you can count on PureVideo _ever_ being available in the Linux drivers. Just look at the KDE4/firefox 3 nvidia debacle; Nvidias Linux drivers are the worst right now: even AMDs linux drivers are more usable / less buggy / incomplete (however, for video playback they are even worse than nVidias).

Software decoding is a safe bet, however. Once we get multithreaded decoding 1080 playback using a fairly cheap processor should not be a problem (just look at Q6600 prices for example; 2,6 GHz quadcore for 160€ / 200$; if we could employ all four cores this should play even high bitrate scenes without _any_ problems).
But as CABAC decoding seems to be very complicated when using multiple threads (and I suspect dull to program) we will have to wait...

-- bedahr

---

### Post by aeiah on 2008-10-13
for the record i have graet 720p x264 playback with my hardware (its software, obviously, as has been stated). my system specs are just: AMD x2 3800 1gb ram nvidia 7800GT. i dont know what specs you'll need for 1080p but mine just about manages it until you hit high action scenes so you should be pretty safe with new hardware.

---


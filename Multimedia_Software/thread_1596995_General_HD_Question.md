---
title: "General HD Question"
date: 2010-10-14
forum: Multimedia Software
---

### Post by ntaforge on 2010-10-14
Hey everybody just a few questions on h.264 or HD playback and editing


So I bought myself a new Sanyo Xacti fh1 1080p camcorder and on my current desktop setup I cannot play full hd back. It uses mp4 format.

Now my setup is a Linux Mint 9 amd64, Intel Core 2 Duo 1.8ghz, 2gb ram, ati hd4650 (proprietary drivers). So my question is, should I change to a Nvida GT220 or is it just my processor can't handle it?

I tried using vlc  I did the compile of mplayer with multicore support which worked for 780p but 1080i was slow and 1080p wasn't working and all of the video editors that I tried didn't work.

What do you all think?

---

### Post by Yellow Pasque on 2010-10-14
If you want video acceleration with ATI proprietary driver, you need an xvba backend for va-api and a player that supports va-api (I'm not sure if mint enables vaapi in their vlc package by default). [http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/)

---

### Post by cascade9 on 2010-10-14
You could try XvBA 

[http://en.wikipedia.org/wiki/X-Video_Bitstream_Acceleration](http://en.wikipedia.org/wiki/X-Video_Bitstream_Acceleration)

How to get it going depends on what media player you are using.....and its probably not goign to work, XvBA is nowhere near as mature as VDPAU. Worth a try though ;)

*edit- beat by Temujin, again. How a blind horse found this thread I dont know :lolflag:

---

### Post by ntaforge on 2010-10-14
Thanks guys for your response!

I think I'm just going to ditch the ATI card. Sad really cause I've always used ATI back in my windows days. But if Nvida supports Linux 100% then Nvida gets the go!

Thanks again

---

### Post by cascade9 on 2010-10-15
I wouldnt say that either of them support linux 100%....ATIs has pretty much washed thier hands of all the cards before HD2XX (RV600 series) but the do support the open soruce driver, as least a little. 

On the other hand, nVidia does tend to keep the cards in support for much longer. They have only just dropped support for the old 71.XX drivers (mainly for pre geforce cards) but they dont support the open soruce drivers  at all.....

---


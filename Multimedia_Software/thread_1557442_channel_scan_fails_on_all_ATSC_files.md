---
title: "channel scan fails on all ATSC files"
date: 2010-08-20
forum: Multimedia Software
---

### Post by garydale on 2010-08-20
I actually have two different computers with two different Haughpage cards, one a 1250 and the other a 2250, but I'm having the same problem with each.

I'm in Toronto on Rogers cable, which may be the problem if Rogers doesn't transmit anything clear. No matter which file in the /usr/share/dvb/atsc/ directory I use for the scan command, I get WARNING: >>> tuning failed!!! on every channel on the computer with the 2250 card.

I get similar results - no channels - if I use Kaffeine to scan on the computer with the 1250 card.

This leads me to believe that I'll need an antenna or a cable box to make this work. Can anyone confirm this?

--------------------------
After attaching a cheap indoor HDTV antenna to the 2250, I was able to pick up a half-dozen channels using the us-NTSC-center-frequencies-8VSB source (ATSC may also work). Most of the channels were variations of Buffalo's WNED (PBS) station and a local CBC station. 

Taking the antenna upstairs and plugging it into the 1250 card, I eventually was able to tune in 8 stations - but not WNED. Most were local Toronto stations, although one was American..

Having verified that the hardware was working however, I went back to trying cable TV. Unfortunately, although one source did give me a lot of channels (and a few others gave me a half-dozen), none of them actually seemed to be work.

I'm not sure why the cable gave me different results than previously unless Kaffeine is now accepting channels it can't decode. However, I'm guessing that this means the local cable provider doesn't distribute anything in the clear. So I'll need a better antenna or a HD cable box to actually use the cards.

---


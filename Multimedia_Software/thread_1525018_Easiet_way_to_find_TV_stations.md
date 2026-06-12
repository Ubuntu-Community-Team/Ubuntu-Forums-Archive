---
title: "Easiet way to find TV stations"
date: 2010-07-06
forum: Multimedia Software
---

### Post by wonderingwhy on 2010-07-06
Hi what's the easiest way to find out if your media card is able to ID TV stations. So far I've had no luck.

I've tried dvbtune and this is what I get:

scan /usr/share/dvb/dvb-t/
scanning /usr/share/dvb/dvb-t/
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: initial tuning failed
dumping lists (0 services)
Done.

I'm using a Hauppauge WinTV-HVR-4000 media card. 

Am I missing something obvious; like my coding's pants!

---

### Post by wonderingwhy on 2010-07-06
So this is what I did, I down loaded Zapping TV via ubuntu software centre, and checked through this, and I have channels, not HD, but still I have channels.  At least my TV card is working - this is what I wanted to know.

I had to point Zapping in the direction of the right device though - which for me is /dev/video1   /dev/video0 is what I'm using for my webcam.

No sound, but I'm working on that - probably just pointing Zapping to the wrong place.

---

### Post by wonderingwhy on 2010-07-08
Another way I found to test the channels in HD is to do so via Kaffeine - which would be a perfect alternative to MythTV for me - if I could make it have sound, and if HD wasn't so jerky, oh and if I could change channel without having to shut the application down.

Enough about that if you just want a way to check if you can find HDTV stations - Kaffeine is the goer.

---

### Post by johnkjaer on 2011-06-28
> **wonderingwhy said:**
> Hi what's the easiest way to find out if your media card is able to ID TV stations. So far I've had no luck.

I've tried dvbtune and this is what I get:

scan /usr/share/dvb/dvb-t/
scanning /usr/share/dvb/dvb-t/
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: initial tuning failed
dumping lists (0 services)
Done.

I'm using a Hauppauge WinTV-HVR-4000 media card. 

Am I missing something obvious; like my coding's pants!


DVBT is frontend 1

---


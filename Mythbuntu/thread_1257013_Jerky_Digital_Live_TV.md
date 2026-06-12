---
title: "Jerky Digital Live TV"
date: 2009-09-03
forum: Mythbuntu
---

### Post by Weidbrewer on 2009-09-03
I am having an issue where my digital channels for live TV are experiencing jerkiness, some stutter and a little pixalation at times.  (I haven't tried recording something and playing that back...occured to me just now.)

The system is running Ubuntu 8.10 64-bit, with an AMD Athlon 64 X2 4400+ 2.3GHz processor, 4GB of RAM and a Hauppauge 1600 tuner card.  Channels are unencrypted signals comming over a standard cable line.  So far as I could tell, the analog side of the card is playing channels just fine.


Also somewhat related:  When I switch the imput to the digital side of the card, I always have to adjust the screen fill so that it is not displaying in a half-sized box in the middle of the screen.

Anyone have any ideas?

---

### Post by klc5555 on 2009-09-03
> **Weidbrewer said:**
> I am having an issue where my digital channels for live TV are experiencing jerkiness, some stutter and a little pixalation at times.  (I haven't tried recording something and playing that back...occured to me just now.)

The system is running Ubuntu 8.10 64-bit, with an AMD Athlon 64 X2 4400+ 2.3GHz processor, 4GB of RAM and a Hauppauge 1600 tuner card.  Channels are unencrypted signals comming over a standard cable line.  So far as I could tell, the analog side of the card is playing channels just fine.


Also somewhat related:  When I switch the imput to the digital side of the card, I always have to adjust the screen fill so that it is not displaying in a half-sized box in the middle of the screen.

Anyone have any ideas?

With the 1600, I'm always a bit surprised when the digital side works at all ...

But that aside, the digital side of the card seems to have serious signal-strength requirements that the analog side of this card (or any non-Hauppauge digital card I've ever used) does not share. Signal strength issues might account for your pixelation. You might want to check to make sure the cabling is tight all the way to the card on the digital input, and that the cabling leading in to the digital input has been laid out with the minimum amount of splitting upstream (beyond the 2-way you have to use to connect the card's two inputs). The digital half of this card also frequently benefits from a small line-drop amp (Motorola or similar) being inserted somewhere upstream. 

The "half-size box", as a first guess, _might_ be what you're seeing if wide-screen 16x9 program is being letterboxed on a 4x3 SD channel. (?)

---

### Post by Weidbrewer on 2009-09-03
> **klc5555 said:**
> 
You might want to check to make sure the cabling is tight all the way to the card on the digital input

I'll give the connections a try...the pixalation is only part of it, though.  The stutter is very much like playback on a machine that can't handle it - but my hardware should be more than good enough for HD.
> 
The "half-size box", as a first guess, _might_ be what you're seeing if wide-screen 16x9 program is being letterboxed on a 4x3 SD channel. (?)

Well, yes...that's exactly what it is.  I'm wondering how to keep it from defaulting back and causing me to have to reset it every time I watch that tuner.  Sorry for not being clear.

---

### Post by SiHa on 2009-09-03
>  The stutter is very much like playback on a machine that can't handle it - but my hardware should be more than good enough for HD.

I wouldn't be too sure - HD decoding takes a hell of a lot of grunt on non-dedicated hardware. My BE/FE is virtually identical to yours: 8.41, Athlon 64 X2 4200, 2GB RAM, and it stutters when trying to play HD. It can just about handle 720p, but 1080 - forget it.

Regarding the letterboxing, there's a field in the TV playback setup to force the output to a particular ratio, have you played with that?

---

### Post by Weidbrewer on 2009-09-03
> **SiHa said:**
> I wouldn't be too sure - HD decoding takes a hell of a lot of grunt on non-dedicated hardware. My BE/FE is virtually identical to yours: 8.41, Athlon 64 X2 4200, 2GB RAM, and it stutters when trying to play HD. It can just about handle 720p, but 1080 - forget it.

Granted...I guess especially when one takes the recording/playback combo that live TV requires...the two "buts" I have are that 720p files play just fine through the system itself (These are not through the card and don't have the recording drain, obviously) and there is only one HD channel that I have tried - the rest have all been SD digital channels.  

I realize that I let myself slip over to the HD side of things in my last post (Just to assure everyone, I'm not like 90% of people who seem to have gotten misled with the digital change-over to thinking that "digital" and "HD" are the same thing.;))  Sorry for the confusion.

> 
Regarding the letterboxing, there's a field in the TV playback setup to force the output to a particular ratio, have you played with that?

Oh.  Dur.  Yeah, I didn't even think of that.  Haven't had to use that section before, so I forgot it was even there...is that something that different profiles can be set for each of the tuners?  (I'm fairly certain that the answer is "yes.")

---

### Post by klc5555 on 2009-09-03
> **Weidbrewer said:**
> I'll give the connections a try...the pixalation is only part of it, though.  The stutter is very much like playback on a machine that can't handle it - but my hardware should be more than good enough for HD.




A stuttering-like playback problem would normally tend to be a frontend problem, which should be visible in the frontend log with a series of the dreaded "prebuffering pause" entries. The first thing to do would be to work through the prebuffering pause troubleshooting doc on the mythtv wiki [http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause](http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause)

---

### Post by Weidbrewer on 2009-09-03
Aw, crap...had to go through that with one of my frontends a while ago...not fun.

---

### Post by SiHa on 2009-09-03
> there is only one HD channel that I have tried - the rest have all been SD digital channels.
Oh well, probably something else then, time to debug those prebuffering pauses...

> is that something that different profiles can be set for each of the tuners? (I'm fairly certain that the answer is "yes.")

Not sure - it's been over a year since I had to do any real configuring of my system.

---

### Post by Weidbrewer on 2009-09-03
> **SiHa said:**
> 
...it's been over a year since I had to do any real configuring of my system.


Same here...but I just *had* to upgrade, didn't I...:P

Hey, be thankful I'm not asking about getting the FM tuner in that card working...

---

### Post by SiHa on 2009-09-03
> **Weidbrewer said:**
> Same here...but I just *had* to upgrade, didn't I...:P

I know what you mean, I've just picked up a cheap DVB-S card and dish, so I just know I'll be here with questions after a weekend of head-scratching.

---

### Post by williammanda on 2009-09-06
One other thing to look at is the cpu usage during the time of the bad video. If the cpu usage is high then that is a red flag. Also if you have a tv, check the picture quality so you have a reference to your htpc output.
Thanks

---

### Post by davidstoll on 2009-09-06
I changed my playback profile to "slim" and that seemed to fix my problem.  I don't know why because I have a quad core 2.8MHz processor and 4Gigs of ram.

---

### Post by williammanda on 2009-09-06
View your your cpu usage while viewing a HD recording. I open system monitor then start mythtv. While viewing the recording I hit alt + tab to bring up the system monitor. Play with your frontend settings and compare.
Also if you have a Nvidia video card, I would advise installing VDPAU. I have a C2Q 9300 and one core was at 100% while viewing a HD recording and after installing VDPAU the cpu usage went down to 5%. Here is the link:

[http://ubuntuforums.org/showthread.php?t=1063102](http://ubuntuforums.org/showthread.php?t=1063102)

Thanks

---

### Post by Weidbrewer on 2009-09-06
> **davidstoll said:**
> I changed my playback profile to "slim" and that seemed to fix my problem.  I don't know why because I have a quad core 2.8MHz processor and 4Gigs of ram.

Nope, that unfortunately did not clear it up.

**williammanda** - I'm running at fairly consistantly 20% +/- 5% on both cores with only a quarter of my ram in use.

As for logs, I get periodic messages along these lines:

```
2009-09-06 16:57:46.926 [mpeg2video @ 0x7fec9356fe90]invalid mb type in I Frame at 0 16

```

...and mainly get this:

```
2009-09-06 16:57:47.039 [mpeg2video @ 0x7fec9356fe90]end mismatch left=267 2D207
2009-09-06 16:57:49.338 [ac3 @ 0x7fec9356fe90]frame CRC mismatch
2009-09-06 16:57:49.983 [mpeg2video @ 0x7fec9356fe90]slice mismatch
2009-09-06 16:57:50.139 [mpeg2video @ 0x7fec9356fe90]invalid mb type in I Frame at 20 12

```

---

### Post by Weidbrewer on 2009-09-12
Anybody have any ideas?

---


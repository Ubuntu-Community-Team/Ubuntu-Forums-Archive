---
title: "ESD sound not working? Startup sounds...recording...all not working"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by randydueck@mts.net on 2008-03-06
Ok, I've finally done enough scouring of the internet in vain.

Here are my problems:

1. System sounds are not playing. Everything else plays. Related to this (maybe), when Xserver starts (after entering my username and password), the screen goes black with an "X" cursor instead of the normal loading screen with the Ubuntu colours. Other than that, everything starts up and works normally. I don't remember when this problem started, but since upgrading to Gutsy, I've customized my desktop graphically. 

2. When I try to change the master volume with my my mac keyboard, the volume icon appears in the middle of the screen and appears to adjust the volume, but it has no effect on any videos or audio files that are playing.

3. None of the audio production software in Ubuntu Studio properly detects and records guitar sounds through the line in. I can hear unprocessed guitar sounds using Jack, but as soon as a signal gets routed to any audio applications such as guitar effects, i get nothing. I also tried the mic input, but that gives me terrible, poppy garbage.

I would appreciate any informed suggestions.

---

### Post by oskar2000 on 2008-03-09
post the output of:
> $ aplay -l

---

### Post by randydueck@mts.net on 2008-03-23
Here is the output:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
randy@randy-desktop:~$ 


It is a built in sound card on the ASUS M2N-E motherboard.

---

### Post by randydueck@mts.net on 2008-03-30
bump

Perhaps sound really is the greatest weak point of Linux....I haven't heard anyone claim that Linux is great for audio production. I hope somebody can prove me wrong.

---

### Post by ubonetu on 2008-03-30
Studio is great and Ardour, Hydrogen, Audacity...  All pretty amazing tools.  I recorded an album using almost exclusively Ubuntu Studio on an Old Vaio and it kicks ***.

So, there's a small claim.  You may not have checked out Ardour 2 yet.  For free, it's gold, Johnny, gold.

ub:KS

---

### Post by randydueck@mts.net on 2008-03-30
> **ubonetu said:**
> Studio is great and Ardour, Hydrogen, Audacity...  All pretty amazing tools.  I recorded an album using almost exclusively Ubuntu Studio on an Old Vaio and it kicks ***.

So, there's a small claim.  You may not have checked out Ardour 2 yet.  For free, it's gold, Johnny, gold.

ub:KS
On a Vaio, eh? What were the specs, and did you have any latency problems? I'm hoping my built-in sound card on an ASUS M2N-E motherboard will be able to do what it was meant to do, unlike the ridiculous latency windows software is giving me.

I also installed Ubuntu Studio, so I've tried Ardour. However, you may note from my above post that  I haven't gotten to that elementary first step of being able to record an audio signal, so I can't say whether I like it or not. All I can say is that I'm frustrated with Linux sound as a whole, because that is a rather crucial step that generally "just works" in any other operating system.

If I don't find a solution to my broken audio soon, I may have to do a fresh install of Ubuntu, because I really REALLYy want to try Ardour and those cool guitar effects racks.

---

### Post by oskar2000 on 2008-03-30
Sorry for the late reply.

This seems to be an on-board sound card. Googling for the chipset tells me that many people have a problem with that particular sound chip. You can try switching to OSS, maybe they have better support.
As for the latency - the latency is mostly determined by the soundcard, and not the system. Most, if not all sound-on-board cards have a pretty high latency.

I would indeed not recommend linux if you are going to do a lot of audio editing. Ardour is a stable program, but I personally think that the workflow is horrible. However, if you - like me - don't need more than reaper and the Stillwell Plugins for your home-recording needs, linux is just as good. (after a little bit of setting-up) 

I guess the guitar-effects you are referring to is Jesussonic. They are available for windows too, but again - you need a fast soundcard to get usable results. If you want to use linux too, I would recommend m-audio. They are pretty well supported. I personally have an audiophile and a delta1010lt, and they both work well on linux. (master control does not work - you have to attenuate each channel individually - sensitivity settings are not available... both aren't that big of a problem)

As for the software - I would recommend Reaper by Cockos for both Windows and Linux. (The same guys that made Jesussonic)  I switched to Reaper after having used Cubase for a couple of years... so it's not a budget decision. I think it's one of the best, DAW's out there.
There are threads on the Cocks forum that tell you how to install it on linux... it works equally well on both systems.
If you're going to use synthesizers or real-time effects you need a better soundcard. The audiophile is below 100$, and this is probably as cheap as it gets for your purpose.
[http://www.cockos.com/products.php](http://www.cockos.com/products.php)
Many commercial audio plugins come with dongle protection. Those do not work on linux. Many do however. For the start I highly recommend the excellent and free (non-expiring freeware, purchase if you like it) Stillwell plugins:
[http://www.stillwellaudio.com/](http://www.stillwellaudio.com/)

Hope that helps

---

### Post by randydueck@mts.net on 2008-03-30
Thanks a lot - this is probably all the info I need then. I think I'll stick with my 3-year old iBook and Garageband, because it obviously has a better sound card and drivers than my newer, dual-core desktop, which I thought would be a super audio workstation in comparison. 

I guess Macs really are superior multi-media machines. Heck, I can play and record multiple tracks with real-time effects and have no noticeable latency. And I didn't have to fine-tune or change anything. AND it has 1/4 the processing power and RAM. Oh, and what's a sound card? Who cares, it works...

no offense, but Linux isn't doing it for me anymore. It's fun to tinker with once in a while, but it's just not a pleasant or efficient way to get a lot of work done. Tootles.

---

### Post by oskar2000 on 2008-03-30
Exactly... don't touch a running system.

I personally couldn't work with garage band. I fully agree that linux has to catch up in the audio department. But since what I need works well on both systems, I stick with linux.

I do use some pricey dongle protected plugins in a small studio that I run... so linux is not an option there - but even if they did work on linux I probably would not switch because it works the way it is.

You shouldn't generalize it though. Setting it up to run reaper is a matter of minutes for an experienced user... and very doable for a newbie.

---

### Post by randydueck@mts.net on 2008-03-30
wait a minute...is the usb Griffin iMic considered a sound card? probably a dumb question, but if it could provide low latency, I might give this another shot.

---

### Post by oskar2000 on 2008-03-30
Yes... well "sound device" would probably be more appropriate, but yes, it seems to be basically a tiny usb sound card.

---

### Post by english on 2008-03-31
Hi

I'm using a cheap behringer usb soundcard UCA200, after the initial pain of setting up and coming to terms with Jack everything records v good, no latency problems 

unlike when I was using it with Cubase and winXP,

Long live Ardour

---


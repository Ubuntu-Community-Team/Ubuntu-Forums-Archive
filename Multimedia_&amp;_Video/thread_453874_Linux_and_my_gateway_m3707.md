---
title: "Linux and my gateway m3707"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by zitstif on 2007-05-24
I've recently setup my laptop to dual boot either Ubuntu or Vista, and currently I've been using Ubuntu even more then Vista.. primary reason, Ubuntu is so much faster, plus unix/linux distros are just sexy to me.. anyways

my audio device is : 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

Currently it looks like my audio functions, I get the speaker icon.. no errors appear when I run alsamixer in the console. And I've unmuted everything.

But even with all the switches set correctly, and all the volume adjusters set all the way up.. I still have no audio. Any ideas?

I know ATI doesn't have the best support for OSS, but hey.. maybe there's a workaround?

OS: Ubuntu Feisty Fawn


I've tried the methods suggested in the audiodebugging page of ubuntu, but had no luck..


amixer -i
Simple mixer control 'Master',0
Capabilities: pvolume pswitch
Playback channels: Front Left - Front Right
Limits: Playback 0 - 31
Mono:
Front Left: Playback 31 [100%] [0.00dB] [on]
Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
Capabilities: pvolume
Playback channels: Front Left - Front Right
Limits: Playback 0 - 255
Mono:
Front Left: Playback 255 [100%] [0.00dB]
Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'LFE',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined
Playback channels: Mono
Limits: Playback 0 - 31
Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'IEC958',0
Capabilities: pswitch pswitch-joined cswitch cswitch-joined
Playback channels: Mono
Capture channels: Mono
Mono: Playback [on] Capture [off]
Simple mixer control 'Capture',0
Capabilities: cvolume cswitch
Capture channels: Front Left - Front Right
Limits: Capture 0 - 15
Front Left: Capture 0 [0%] [0.00dB] [off]
Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Capture Mux',0
Capabilities: volume
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 4
Front Left: 4 [100%] [40.00dB]
Front Right: 4 [100%] [40.00dB]
Simple mixer control 'Caller ID',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]
Simple mixer control 'Input Source',0
Capabilities: enum
Items: 'Mic' 'Front Mic' 'Line'
Item0: 'Front Mic'
Simple mixer control 'Off-hook',0
Capabilities: pswitch pswitch-joined
Playback channels: Mono
Mono: Playback [off]



amixer scontrols
Simple mixer control 'Master',0
Simple mixer control 'PCM',0
Simple mixer control 'LFE',0
Simple mixer control 'IEC958',0
Simple mixer control 'Capture',0
Simple mixer control 'Capture Mux',0
Simple mixer control 'Caller ID',0
Simple mixer control 'Input Source',0
Simple mixer control 'Off-hook',0

alsamixer has all options all topped out, and nothing is on mute

ALSO.. another odd problem.. my mouse is "jumpy" when i'm typing something the point of focus will often switch to another point.. and i think it's my mouse, but it's hard to tell..

---

### Post by Skisher321 on 2007-05-31
Have you gotten any response to this in any way?  I'm having the exact same problems, including some massive internet problems on the m3707 that I wasn't having with Vista.:(

---

### Post by zitstif on 2007-06-01
Nope.. nothing

---

### Post by zitstif on 2007-06-04
[http://ubuntuforums.org/showthread.php?t=415821&page=3](http://ubuntuforums.org/showthread.php?t=415821&page=3) 

this might be helpful.. wasn't helpful to me.. but for some odd reason I believe this is more of a m3703 chipset specific problem.

---

### Post by zitstif on 2007-06-14
Anyone have any luck?

---

### Post by zitstif on 2007-06-29
Sounds like the best fix is to go to the previous version of Ubuntu.

Hope that works for some one.

---

### Post by zitstif on 2007-07-13
anyone get this to work on feisty fawn?

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

---

### Post by cyb3rpeace on 2007-07-16
> **Skisher321 said:**
> Have you gotten any response to this in any way?  I'm having the exact same problems, including some massive internet problems on the m3707 that I wasn't having with Vista.:(

I did not like the realtek wireless that came with this laptop so i got a Intel wireless 2200 card and replaced the realtek, wireless performance much better. Best $10.00 i have spent in a while 


> **zitstif said:**
> Sounds like the best fix is to go to the previous version of Ubuntu.

Hope that works for some one.

Does the sound work with the previous version?

---

### Post by zitstif on 2007-07-18
[http://ubuntuforums.org/showthread.php?t=415821&page=3](http://ubuntuforums.org/showthread.php?t=415821&page=3)

According to this source 

seems like it works with edgy eft

btw have you tried this?

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

I'm going to give it a shot.. see what happens.. feels like i've done it before

---

### Post by zitstif on 2007-07-22
Btw.. this method did not work for me.. Still no sound..

can't recall how long it has been that i haven't had sound...


Well if I'm desperate enough to have sound.. I'll go back to edgy but for now.. I'll work without sound.. 

As in they say in counter-strike.. sound is for the weak!! lol (jp)

I love linux.. but there are some headaches I've been dealing with..


Btw.. but from my experience.. KUBUNTU sucks!! it's true.. ubuntu rocks kubuntu...

---

### Post by cyb3rpeace on 2007-07-23
I have tried all kinds of stuf to get the sound working. I loaded the edgy eft live cd and still nothing.

Ah well i am getting used to life without sound.

---

### Post by zitstif on 2007-07-23
Well that tutorial didn't help....

Anyone have any luck yet? Am I just missing something?

---

### Post by zitstif on 2007-08-06
[up]

Still no sound till this day, still running feisty fawn.

I would really appreciate some input from anyone else.

I really love ubuntu, and linux in general, but let's get realistic people, a person who is not tech-savy does not want to spend hours.. or days.. trying to fix a problem.

(I'm pretty tech-savy.. no guru.. but an A+ certified tech, and just generally understanding and patient)

I'm sure cyb3rpeace and I would appreciate some more input.

---

### Post by zitstif on 2007-11-02
[http://www.amazon.com/Eforcity-Adapter-Internet-phones-programs/dp/B000JCQUWQ](http://www.amazon.com/Eforcity-Adapter-Internet-phones-programs/dp/B000JCQUWQ)


This is what I'll be forced to buy for my sound to work on my laptop under linux. 

Running Ubuntu 7.10

Still no sound


am I just an idiot?

---


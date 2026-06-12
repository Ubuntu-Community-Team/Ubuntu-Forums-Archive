---
title: "Audacity lags. Compared click track to metronome"
date: 2010-09-26
forum: Multimedia Software
---

### Post by kerryhall on 2010-09-26
This program rules. However, there is a small problem. My computer lags. I generated a click track, then compared it to a metronome. My computer can not simply play an audio track without lagging. Obviously, for recording this is a huge problem. Brand new fresh install of Lucid.

How do I fix this?

---

### Post by kerryhall on 2010-09-28
Bump.

---

### Post by cchhrriiss121212 on 2010-09-29
Look at the section called real time support in [this guide]("https://help.ubuntu.com/community/UbuntuStudioPreparation"). I don't know whether it will help for sure, but it is worth a shot.

If you are recording music seriously then you may want to look into something more capable, Audacity is a good editor but beyond that it is basic.

Have you tried jack and Ardour or Qtractor? They are both great for multi-tracking, and jack will give you solid low latency performance.

---

### Post by kerryhall on 2010-09-30
Thanks for replying! I have not tried Ardour or Qtractor yet. I think I will give them a try! When you suggest using jack, do you mean uninstalling pulseaudio and using jack instead? And I will check out that link you posted and report back.

Thanks again!

---

### Post by cchhrriiss121212 on 2010-09-30
Jack can be installed alongside pulse, so there is no need to remove anything. When you start jack pulse is suspended, so any regular programs will have no sound ie firefox.
Be prepared for a learning curve though, as jack is complex to new users. It is a modular setup which means you can map your audio anywhere you like.
The biggest issue with jack is that it is non functional out of the box for most users. You should get a dialogue box that asks you about setting up realtime access when you install jack, which is the same stuff I linked you. 

What do you record if you don't mind me asking? There are lots of neat linux apps out there for music production.

---

### Post by tgalati4 on 2010-09-30
Does your metronome have a calibration screw?  Just as instruments need tuning, your clocks need syncing.  This is normally done with a Master Clock Sync cable.

---

### Post by kerryhall on 2010-09-30
The metronome is a standalone, electronic one. I would imagine that it uses a crystal for reference.

---

### Post by tgalati4 on 2010-09-30
If you play back two CD players with the same track, they will drift as well.  The quartz crystals used to maintain the 44.1 KHz sampling frequency will drift over time (+/- 0.5% I believe).  This results in pitch differences; normally not noticeable until you try to mix tracks.  Then you get phase shifting/cancellation and after enough time, the beat longer tracks.  

If you open your metronome, you will probably see a +/- potentiometer.  Calibrate it to your audacity click track and you will be OK for the next few hours.

---

### Post by kerryhall on 2010-10-01
Wow, I did not know that! I thought the crystal maintained an accuracy of something that wouldn't be detectable to the human ear, but I guess it compounds and you end up with drift.

So Audacity probably isn't lagging at all, lol.

---

### Post by tgalati4 on 2010-10-01
It wasn't an issue until folks such as yourself started to mix digital tracks and found weird phase effects because of clock mismatch.  Check PreSonus, M-Audio, or any other digital gear and you will find Master Clock Sync connections.  

There are ways to speed up or slow down computer system clocks so that they sync with each other.  ntp (network time protocol) has advanced features that allow you to get within 0.001 seconds of the master US atomic clocks.

That won't help you with your metronome, but at least you will have the correct time.

---

### Post by kerryhall on 2011-08-24
> **cchhrriiss121212 said:**
> 
What do you record if you don't mind me asking? There are lots of neat linux apps out there for music production.

Sure! Sorry it's taken a year to reply haha. I'm working on building guitar amps and I would like to record how they sound. Also when I jam on guitar it's hard to remember what I play so it's nice to have recordings of anything interesting I come up with. 

I haven't actually had a chance to record anything in awhile. I was having performance issues with my laptop, so I installed fluxbox instead of metacity, and things are running MUCH faster now. (also using slim, thunar, midori, and xterm)

---


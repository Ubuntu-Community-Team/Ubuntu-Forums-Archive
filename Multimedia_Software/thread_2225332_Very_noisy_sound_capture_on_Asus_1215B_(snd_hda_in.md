---
title: "Very noisy sound capture on Asus 1215B (snd_hda_intel driver)"
date: 2014-05-21
forum: Multimedia Software
---

### Post by sangief on 2014-05-21
Hi everyone,

I'm trying to capture sound from an external source (an electronic drum kit which I connect through the microphone plug) but the input level is always too high, which makes the capture extremely noisy and unusable. I've tried several things (like tweaking the model option or the position_index of snd_hda_intel inside alsa-base.conf), but none succeeded. I've even installed the newest version of the Realtek driver. I've also tried capturing sound from my cellphone and the exact same thing happens, which means that the drum kit is not the issue.

I would really appreciate any help, since I'm clueless here. I attach the output from the alsa-utils-alsa-info.sh script for further details of my system.

Thanks in advance!

---

### Post by Yellow Pasque on 2014-05-21
Try turning down Mic Boost?

```
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [36.00dB]
  Front Right: 3 [100%] [36.00dB]
```

---

### Post by sangief on 2014-05-21
Nope, that doesn't help at all :(

---

### Post by Yellow Pasque on 2014-05-21
Have you tried lowering the mic vokume? (It looks like you have it at maximum.)

Also, You're using the custom Realtek module/driver
```
Driver version:     1.0.2x-130606-v5.18rc7
```

Does the same thing occur when using the regular kernel module/driver?

---

### Post by sangief on 2014-05-21
Yes, I tried changing mic volume, mic boost and every other related parameter (using alsamixer).
I installed that driver recently because of this issue. It happens with both the regular driver and this one...

---

### Post by Yellow Pasque on 2014-05-21
Maybe your model needs a quirk like: [https://github.com/torvalds/linux/commit/2cede30379f3fed3f4c83010cf08be6afcc811b9](https://github.com/torvalds/linux/commit/2cede30379f3fed3f4c83010cf08be6afcc811b9)

You'll probably have more luck asking ALSA dev list or making a bug report on kernel bugzilla (Make sure you remove Realtek driver and go back to standard driver before doing that).

---

### Post by CraigPid on 2014-05-22
Do you have a line in input you could use instead. Your drum kit is probably already being amplified before it goes in the mic input. If you don't have a line in and you're serious you could get a cheap usb audio interface for probably under $30 or a great pci card like the m-audio 24/96 for around $100. I've found that onboard sound on motherboards has improved in recent years but there's no comparison to a quality audio card. Depends what you want it for of course but if you're into recording or performing then shelling out a few bucks is the way to go.

---

### Post by CraigPid on 2014-05-22
Just a comment here.. I was looking up your laptop and it seems to kind of verify my last comment. Sound is basically an afterthought in computers. You can't really even find much info on the audio in that laptop. I suppose most computers are used in offices and so on today and the're connected to cheap speakers so manufacturing the computer with a quality audio device would probably put the price out of range of the target consumers.

---

### Post by tgalati4 on 2014-05-23
Sounds like you need a Line-In to Microphone-Level attenuator.  You can either make one or buy one:

[http://www.bhphotovideo.com/c/product/1004663-REG/pearstone_ila_123_in_line_attenuator_for_m.html](http://www.bhphotovideo.com/c/product/1004663-REG/pearstone_ila_123_in_line_attenuator_for_m.html)

---


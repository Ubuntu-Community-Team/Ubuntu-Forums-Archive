---
title: "Poor sound quality on Ubuntu"
date: 2010-05-31
forum: Multimedia Software
---

### Post by Puggytree on 2010-05-31
Since installing Ubuntu I've always had shocking sound quality, I thought it was my cheap speakers so used my headphones which turned out to be worse (And they aren't bad headphones) and since there was the upgrade coming out I didn't dig too much into finding a solution hoping 10.04 would have sorted it.

Anyway I've tried looking for the drivers and if I use aplay -l it tells me this:

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]

Which I assume means that the driver is installed.. I've tried changing the settings to get a better quality but this hasn't worked either...

Any ideas of what I can do? Even on low settings I get distortion :(

Cheers
Pug

Sorry, turns out alsamixer had been reset to defaults fixed now :)

---

### Post by Eddie Wilson on 2010-05-31
I also have the nvidia setup and my sound is great. It always has been in Ubuntu. If may help if you post the complete specifications of your system. Also have you tried another distro?

---

### Post by Puggytree on 2010-05-31
Hey sorry I'm fairly new to Ubuntu, I really just use it for downloading/web browsing and a bit of word processing (And why pay £70 for 7 when this is free and faster/prettier/more fun) so I haven't really looked at other distro's 

But I seemed to have solved it... Messed around a bit with alsamixer and it seems to have fixed now... Tried this before and it didn't seem to have any effect.. But it's near perfect as they will get with these speakers.. Until one of them packs in while I type xD

But Limp Bizkit sounds good loud :guitar:

---


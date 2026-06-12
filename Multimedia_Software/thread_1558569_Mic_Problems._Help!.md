---
title: "Mic Problems. Help!"
date: 2010-08-22
forum: Multimedia Software
---

### Post by RevGross13 on 2010-08-22
Alright, so long story short, my laptop got a virus, had to wipe the hard drive, and the recovery discs are nowhere to be found, so I'm running Ubuntu 10.04. It's mostly been a smooth transition, except....

My built-in webcam's having problems. I can use the microphone by itself a-ok. I can use the cam by itself a-ok. But if I try to do video, with both the mic AND the cam running, the mic stops working and won't come back until I reboot the entire system.

Like, in Skype, I can make a call ok, but if I try to video chat, there's no sound. And if I try to do a video in Cheese, it freezes up. And that too makes the mic stop working.

I have no idea how to fix this. And I've already tried the PulseAudio thing where you drag one side down to zero, that didn't work. And I told Skype not to automatically adjust my mixer levels, too.

And when I compared all of the levels on the System Preferences / PulseAudio / ALSA before and after trying video, the only thing I saw different was, in the System Preferences, the connector changed from 'Microphone' to 'Line-in', and changing it back didn't fix it, the only thing that ever seems to work is a complete restart.

I have an HP Pavilion Entertainment Notebook dv7-3165dx, and I'm running Ubuntu 10.04. Just in case that matters.

Help me!

---

### Post by RevGross13 on 2010-08-22
Bump...? I'd really like to get this working

---

### Post by HeadHunter00 on 2010-09-05
dv7 huh? i have dv6000, and everything works fine. did you install oss recently? cause if you did, uninstall it. btw, by oss i mean oss base, not alsa-oss. i had your problem before. and for cheese, try deleting the configuration directory, .cheese in your home folder. press ctrl + h to show hidden files.

---


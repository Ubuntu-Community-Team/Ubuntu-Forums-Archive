---
title: "Sound problems with Intel 82801G (ICH7 Family) chipset on a Toshiba laptop [Solution]"
date: 2008-11-03
forum: Multimedia Software
---

### Post by ejsing on 2008-11-03
Hi, this post is to let other users know about my problem, and how I eventually solved it. I spent 6 hours last night trying to get my sound working in Ubuntu 8.10 on my Toshiba laptop.

First of all, everything appeared to work fine. Modules loaded into kernel, alsamixer settings were unmuted and maxed out, hardware buttons for muting/unmuting and sound levels were fine. Still no sound was produced, no matter what I did.

I eventually gave up on solving the problem just yet and rebooted my computer into Windows from hibernation (I know - shame on me). I realized that after booting Windows, the sound on my laptop was muted. Using the hardware mute/unmute button I reactivated it _in_ Windows. And yes you guessed it - after rebooting into Ubuntu this morning, sound is working perfectly!

It would seem that for some reason the sound hadware being muted in Windows, then hibernating, blocks the sound hardware in Linux. I stretch that I was able to use my hardware mute/unmute buttons just fine in Linux prior to rebooting into Windows.

I realize that this has most likely nothing to do with Ubuntu and is more likely to be a kernel bug (or hardware bug for that matter), but I thought I'd present this issue in the forum for the record.

Have a great day, and may all your sound problems magically disappear.

-Simon Ejsing

---


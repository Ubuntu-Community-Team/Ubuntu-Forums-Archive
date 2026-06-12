---
title: "Howto &quot;Fix&quot; Sound in Gutsy (especially with World of Warcraft)"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by Ghost|BTFH on 2007-10-26
For most people, a standard install of Ubuntu Gutsy works fantastic, and there's no issues.

Then there's the weird people like me.

I have such an odd assortment of programs on my system, eventually I run into an issue. In this situation, the issue was, sound was acting up on rare occasions, only on certain programs, especially on World of Warcraft through wine, and I was trying to figure out why a perfectly healthy fresh install would have such crappy sound support!

Well, I found my answer with a couple quick searches inside SOUND (Found under System - Preferences - Sound) where I discovered I had 3 options for my sound:

ALSA
ESD
OSS

Awesome! But wait! ESD is installed (sort of, it's buried in a bulk package) but OSS and ALSA? I did a quick check in Synaptic to find out that NO, ALSA and OSS are not installed!

Installing ALSA (as my preferred choice of sound) and ASLA-OSS fixed everything.

Sound now works great, and I even have sound working QUITE smoothly in World of Warcraft (a MAJOR headache for some, or so I've noticed) after reconfiguring wine (winecfg) under AUDIO tab to use ALSA only.

I hope this helps some others who have been puzzled over sound issues in Gutsy. I know if it's happened to me, it's happened to somebody else out there. :)

Cheers,
Ghost|BTFH

---

### Post by cobb28 on 2007-10-26
Thank you.  Fresh install of Gutsy and wow.  Wow crashed the first time after the sound started skipping. I just installed the also-oss package and all seems ok now.

---

### Post by Spoone on 2007-10-26
I hate to be a party pooper, but this didn't work for me.  I still have no sound in WoW..

---


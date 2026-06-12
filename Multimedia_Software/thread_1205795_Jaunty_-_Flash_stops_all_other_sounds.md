---
title: "Jaunty - Flash stops all other sounds"
date: 2009-07-06
forum: Multimedia Software
---

### Post by BrandonLC on 2009-07-06
I had this problem fixed prior to my upgrade, but the fixes are not available on Jaunty. I've read a lot of information so far, some has fixed other sound issues, some has created more so I backed out of those changes. Nothing has fixed this specific problem.

I've been through a great deal of google searches with no luck. The problem is any time a flash object is loaded into the browser, most sounds stop. I can hear sound produced by the Flash object if it has sound. Though all other sounds, like music I might be playing, stop until I shut the browser down. It's really annoying. Got any adice?

Thanks.

---

### Post by lovinglinux on 2009-07-06
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by BrandonLC on 2009-07-06
Nice. Thanks. This stuff is frustrating. It seems to be working now for the most part. 

Just out of curiosity I tried LinDVD too. It won't work if Firefox is open and it's loaded a Flash object. You have to close Firefox before it can use the sound device. It's not a big deal since I never watch DVD's on this machine, but it's annoying there have been new sound issues with each Ubuntu upgrade.

---

### Post by lovinglinux on 2009-07-06
> **BrandonLC said:**
> Nice. Thanks. This stuff is frustrating. It seems to be working now for the most part. 

Just out of curiosity I tried LinDVD too. It won't work if Firefox is open and it's loaded a Flash object. You have to close Firefox before it can use the sound device. It's not a big deal since I never watch DVD's on this machine, but it's annoying there have been new sound issues with each Ubuntu upgrade.

You might also check "System >> Preferences >> Sound" and change the sound options to ALSA. I'm currently using ALSA, Autodetect, Autodetec, but I removed pulseaudio and installed esound, so setting may vary.

---

### Post by BrandonLC on 2009-07-06
Ya, I was actually using ALSA prior to the upgrade, but it seems be problematic than PulseAudio on this upgrade. I'll mess around with it more, after I enjoy the 95% of sound I worked so hard for for a while :)

---


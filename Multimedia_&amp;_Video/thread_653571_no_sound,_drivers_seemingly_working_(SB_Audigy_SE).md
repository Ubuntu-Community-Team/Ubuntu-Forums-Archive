---
title: "no sound, drivers seemingly working (SB Audigy SE)"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by deleopario on 2007-12-30
I just installed Ubuntu, and I have a Sound Blaster Audigy SE card. Ubuntu seems to be acting like the sound is working fine, but no sound is coming out. The speakers are on and plugged in and all of that (dual booting with XP, sound works fine with it). A couple of times I rebooted and the sound just randomly worked, and then it didn't again. I suspect alsa or oss or whatever I'm using just isn't getting loaded or there's some conflicting process, but I don't know enough about Linux to figure this out.

---

### Post by steefjeqv on 2007-12-30
Hi,

Does your motherboard have onboard sound ?

If so, then there's the possibility that your onboard sound is used in stead off your Soundblaster card (even when it's disabled in your bios).

Have a look at this page :

[https://help.ubuntu.com/community/SoundTroubleshooting#head-72023a784829d5d128546a6092d67062ab50dfea]("https://help.ubuntu.com/community/SoundTroubleshooting#head-72023a784829d5d128546a6092d67062ab50dfea")

In particular : Configuring default soundcards / stopping soundcards from switching

Greetings,
Steven

---

### Post by deleopario on 2007-12-30
This appears to have worked, thanks!

Caveat to any other noobs who find that article though: 
cat /proc/asound/modules will return names with underscores (at least it did for me), but you have to use hyphens instead when you put them in /etc/modprobe.d/alsa-base, that caused me some problems at first.

---


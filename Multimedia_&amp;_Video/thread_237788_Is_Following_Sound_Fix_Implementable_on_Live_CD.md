---
title: "Is Following Sound Fix Implementable on Live CD?"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by GregA on 2006-08-16
I have a Lenovo 3000-N100 Laptop which has no sound (Intel digital SoundMax audio) via the Ubuntu 6.06 Live CD.   I found this probable solution on these forums (see below)- but to implement, it requires a re-boot.   For the time being, I am just using the Live CD.   Is there some way to implement this fix using the Live CD - to make the modprobe file changes persistent?  (see fix below:)

                         * * * * * * * 

 Default  Re: No Audio with: SoundMAX Integrated HD Audio
I have found a solution for my M2NPV-VM mobo.

Not sure how that could apply to laptop cases but as I can see people are looking for generic High Definition audio "soundMAX ADI AD1986A" fixes.
Here is my case description and solution details.

Basically everything is simple (after I spent almost a week looking for answers ).

-Update BIOS (not even sure if that is required step, but it generally always good idea to do that).
-Get latest ALSA drivers. I got "1.0.12rc1" but "1.0.11 final" should also do.
-Put "options snd-hda-intel position_fix=1 model=3stack" to "/etc/modprobe.d/alsa-base".
-Worked for me after reboot.

Good luck.
-Chumba
Reply With Quote

---


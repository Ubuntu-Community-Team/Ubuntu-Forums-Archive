---
title: "spdif: why is it so hard?"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by justDIY on 2007-08-24
Why is it so hard to get SPDIF output working under linux?

I don't think it's a failing of any specific distro, it's probably Intel or Microsoft's fault... but anyway.  I'm fed up fiddling, and I just want to throw money at the problem.

Are there any sound cards that I can buy that the SPDIF output will work plug and play, under linux?  Right now I have tried both nforce2 and nforce4 sound cards, as well as three different creative labs cards (sb live, sb live 5.1 and sb pci128).  None of them are working for spdif output.

I've tried fiddling with alsamixer, asoundrc, oss, nvsound, blah blah blah.  None of it's working.  I briefly got the nforce4 board working, but updated something and it stopped working - I have not been able to recreate the functionality.  I see the forum is filled with dozens of unanswered posts regarding spdif.  There are also a few that are answered, and the suggestion is always the same.  Unmute the IEC985 playback in alsamixer, and use mplayer -ao alsa:device=hw=0,2 (the numbers change, but the suggestion stays the same).  Sometimes device=spdif is suggested, usually in concert with changes to .asoundrc

Current system:  Shuttle SN41G2 PC; with the SOUNDSTORM chip.  Ubuntu 7.04, 2.6.20-16-generic kernel.

All suggestions are appreciated!

---

### Post by buntmebaby on 2007-10-09
I have the same problem and have not TRIED to solve it properly yet, as I know it will involve yelling, screaming, throwing and most of a weekend.

Nforce2 chipset, SPDIF speakers.

Anything these guys did help?
[http://ubuntuforums.org/showthread.php?t=560923&highlight=spdif](http://ubuntuforums.org/showthread.php?t=560923&highlight=spdif)

---

### Post by Soarer on 2007-10-09
I have spdif on board my Gigabyte mobo and it just worked in Gutsy. I could never get it working with my Extigy - Creative AFAIK don't release drivers for us.

May be worth d/ling Gutsy beta & trying the live CD?

---

### Post by Iceni on 2007-10-09
Works out of the box with my nforce4-based asus mobo and feisty.

---

### Post by exactopposite on 2007-10-23
> **Iceni said:**
> Works out of the box with my nforce4-based asus mobo and feisty.

that's good to hear. i just setup an nforce4 machine that i plan on using to play audio thru my surround sound system. i was really hoping spidf would work properly. i'll know for sure later this week.

---


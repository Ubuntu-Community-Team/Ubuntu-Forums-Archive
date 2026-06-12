---
title: "alsamixer showing wrong card"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by guernicaaa on 2007-05-17
okay, I've been through the comprehensive sound guide multiple times, done most everything in it but compile the drivers and reinstall ubuntu.  here's the list of cards I get when I do "Change Device" in my sound control panel
0: M-Audio Delta 1010LT (Alsa Mixer)
1: Audigy 2 ZS [SB0350] (Alsa Mixer)
2: Nvidia CK8S (Alsa Mixer)
3: SAA7134 (Alsa Mixer)
4: ICE 1712 - multitrack (OSS Mixer)

I want the Audigy 2 to be my main card.  I don't want any of the others loaded.  How do I do this?  
I edited
/etc/modprobe.d/alsa-base

the very last line is
options snd-emu10k1 index=0
and I commented out the other sound options that was in there.  but when I run alsamixer, the chip that shows up is the M-Audio Delta.  How do I change this?  I'm not getting ANY sound.

---

### Post by guernicaaa on 2007-05-19
bump
help please?!

---

### Post by CREEPING DEATH on 2007-05-19
Are you trying to use a PCI sound card instead of the integrated?  If you are, disable any on-board in the BIOS.  That will cut down on issues.  Of course, the sound doesn't work on the machine I'm on, but I think the MoBo is bad.

CD

---

### Post by guernicaaa on 2007-05-20
yes, I'm trying to use a PCI card.  disabling doesn't do much, I still get the other PCI card, the M-Audio Delta.  Any way I can uninstall them from the operation system so they're "not there"

---

### Post by accensi on 2007-05-20
Use alsaconf to define default card.

See forum thread [http://ubuntuforums.org/showthread.php?t=418360&highlight=asoundconf](http://ubuntuforums.org/showthread.php?t=418360&highlight=asoundconf) for a recipe.

---

### Post by guernicaaa on 2007-05-20
wow, thanks a million!  worked perfectly :D

---


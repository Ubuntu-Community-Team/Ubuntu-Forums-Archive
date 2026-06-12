---
title: "intrepid sound problems, especially in flash"
date: 2008-11-18
forum: Multimedia Software
---

### Post by le_vainqueur on 2008-11-18
I had sound problems when I first installed Intrepid (clean install).  I got no sound at all until I I changed the devices in System->Administration->Sound all to "HDA Intel STAC92xx Analog (OSS)."  Sound now works except for in two cases, which are:

1. When playing audio from more than one source at a time.  For example, I can play music in Rhythmbox, but if I try to play a movie in VLC at the same time, VLC will have no sound.  If I quit Rhythmbox first, though, VLC will play with sound correctly.

2. There is no sound in Flash videos (ie. YouTube) regardless of whether or not there is another program trying to play sound.

What should I do?

---

### Post by Ng Oon-Ee on 2008-11-18
Sounds like your Pulseaudio setup isn't working properly. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=843012") for a very comprehensive way to trouble-shoot. Post any questions you have here.

---

### Post by gandaran on 2008-11-19
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by le_vainqueur on 2008-11-23
> **Ng Oon-Ee said:**
> Sounds like your Pulseaudio setup isn't working properly. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=843012") for a very comprehensive way to trouble-shoot. Post any questions you have here.

One problem I have right away, is determining what the device should be set to in this step: 
> Click File/Change Device and make sure you have the correct device chosen.
I do not have a sound card, only the motherboard.  I have selected HDA Intel (Alsa mixer), but I am not sure it is correct.

---

### Post by le_vainqueur on 2008-11-23
> **gandaran said:**
> [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

This guide got my sound working in every application I've tested so far.  Thanks for the link!

---

### Post by Ng Oon-Ee on 2008-11-23
> **le_vainqueur said:**
> One problem I have right away, is determining what the device should be set to in this step: 

I do not have a sound card, only the motherboard.  I have selected HDA Intel (Alsa mixer), but I am not sure it is correct.

Yes, that is normally correct for a built-in soundcard with your motherboard.

Basically that test is to ensure that your hardware is working. Do you get sound from that?

---

### Post by le_vainqueur on 2008-11-25
Ng Oon-Ee,

Yes, I did get sound with that test, but not with the other devices in the menu.  I now have PulseAudio working correctly (thanks to this thread), so my sound problems are fixed.  Thanks for all your help.

---

### Post by Ng Oon-Ee on 2008-11-25
> **le_vainqueur said:**
> Ng Oon-Ee,

Yes, I did get sound with that test, but not with the other devices in the menu.  I now have PulseAudio working correctly (thanks to this thread), so my sound problems are fixed.  Thanks for all your help.

You're welcome. Have fun with your fully-working sound system :guitar:

---

### Post by SanjoEel on 2009-01-16
Thanks, this got the sound working in Flash apps for me. :guitar:

---


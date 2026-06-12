---
title: "No sound on toshiba sattelite, hda-intel soundcard"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by Jeff Sell on 2007-07-14
I'm running Feisty on a Toshiba Satellite laptop, and I'm completely unable to get any sound whatsoever when using Ubuntu. I've reinstalled and patched everything ALSA related. I've also fixed the DSDT so that it shows no errors. 
My sound card:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```
I've followed the instructions for fixing sound from the following links: [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
[http://ubuntuforums.org/showthread.php?t=440251](http://ubuntuforums.org/showthread.php?t=440251)
[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)
[http://forum.ubuntu-fr.org/viewtopic.php?id=115326](http://forum.ubuntu-fr.org/viewtopic.php?id=115326)
[http://forum.ubuntu-fr.org/viewtopic.php?id=117422](http://forum.ubuntu-fr.org/viewtopic.php?id=117422)
[http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html](http://www.linuxforums.org/forum/peripherals-hardware/96259-toshiba-p100-series-sound-fix-ubuntu.html)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)
[http://www.linuxquestions.org/questions/showthread.php?t=567376](http://www.linuxquestions.org/questions/showthread.php?t=567376)

None of these have gotten me anywhere, except for turning off the acpi. That gives me sound from music files at a lowered volume, but nothing else (flash videos, etc.) My sound is most definitely not muted. 

When I run ```
sudo modprobe snd-hda-intel
``` nothing happens. No error message, but no nudge of encouragement from my terminal either.

---

### Post by isaacj87 on 2007-07-14
Check to see if there are any updates...I recently put fiesty on my girlfriend's comp (toshiba satellite a105) and it didn't have sound on the fresh install...once I performed an update it worked perfectly.

---

### Post by Jeff Sell on 2007-07-14
Will do.

---

### Post by Jeff Sell on 2007-07-14
No luck, I'm afraid. Was there some specific update? I just went through the update manager, maybe I did it wrong.

---

### Post by ev5unleash1 on 2007-07-14
Yea, try more updates if not then search or ALSA or INTEL audio drivers depending on what kind of audio card it is.

---

### Post by Jeff Sell on 2007-07-14
I downloaded, installed, and compiled the alsa drivers and such about three hours ago. Is there an update floating somewhere else I may have missed? How might I get that?

---

### Post by lisati on 2007-07-14
> **isaacj87 said:**
> Check to see if there are any updates...I recently put fiesty on my girlfriend's comp (toshiba satellite a105) and it didn't have sound on the fresh install...once I performed an update it worked perfectly.
Ditto  but on an A100 - I also needed to turn up the volume and unmute

---

### Post by lisati on 2007-07-14
> **Jeff Sell said:**
> I downloaded, installed, and compiled the alsa drivers and such about three hours ago. Is there an update floating somewhere else I may have missed? How might I get that?

You might have an orange notification icon on the top panel if there are updates that you system has managed to find out about for itself. If its there, double click on it.  Failing that, you can use the system->administration->update manager menu.

---

### Post by Jeff Sell on 2007-07-14
It says that my system is up to date.

---

### Post by ev5unleash1 on 2007-07-14
Make sure the audio card is some intel and make sure that on the sound manager that the audio card that is select is ALSA

---

### Post by Jeff Sell on 2007-07-14
The audio card is definitely hda-intel ICH7 chipset. I doubled checked the sound manager; everything is ALSA.

---

### Post by ev5unleash1 on 2007-07-14
is the sound nob up and on everything the volume is up. Make sure that you restarted since everything and that you are up-to-date with the update manager. If none of those suggestions work try to look for another ALSA driver you something you may of missed.

---

### Post by isaacj87 on 2007-07-14
Yeah...i noticed that after I updated i had to make sure all the volumes were up.

---


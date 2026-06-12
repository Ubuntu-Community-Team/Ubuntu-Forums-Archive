---
title: "pulseaudio volumemeter ok but no sound"
date: 2009-10-20
forum: Multimedia Software
---

### Post by rubikon on 2009-10-20
Recently set up dualboot on old PC and recent laptop with XP & Ubuntu - been to hell and back but learnt a lot - laptop now perfect with 9.04 - PC ok with 8.1 apart from 1 thing ....the sound.
Realise I have a creative soundblaster audio pci 128 which seems to be one of the worst options:( but that said , I have followed the marvellous instruction guides from 'gods' psyche83 and markubuntu i.e. I've installed pulseaudio and everything appears to be as it should be (though psyche83 advises autodetect plus alsa options in 'Sound' whereas marku advises pulseaudio and soundcard) yet the volumemeter shows sound and thinks its playing yet no sound. Tried tinkering with the permutations but no joy - anyone any ideas?

(By the way the sound works fine if I boot back into XP so the connections/card/speakers are obviously OK.)

TIA
Rubikon

---

### Post by rubikon on 2009-10-20
forgot to mention - the volume control shows -20db ....does this sound(sic) right ?

---

### Post by rubikon on 2009-10-21
[SIZE=2]Many thanks to all who have painstakingly compiled their hints,tips& user guides :              
it was a couple of lines in thread 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
which finally solved it for me - thanks to 
======================================================
[/SIZE]
[LIST]
[*][SIZE=2]**shaviro** found the following from this post [/SIZE][[SIZE=2]http://www.ubuntuforums.org/showthread.php?t=153752[/SIZE]]("http://www.ubuntuforums.org/showthread.php?t=153752&highlight=touchpad+sony")
[/LIST]
[SIZE=2]     Quote:
                                                 I wasn't getting any sound out of my Sony Vaio PCG-4B1L ...                                 
[/SIZE]     Quote:
                                                 [SIZE=2]The crucial thing is to enable everything in alsamixer EXCEPT "external amplifier." (I had to turn off microphone too, to stop feedback).

==================================================
Not strictly true it was ticking the box IEC958 in ALSA mixer that actually did it for me - other tick boxes didn't matter.
One thing I've learnt about the marvellous UBUNTU in the last month of pain is that it can be all things to all men ,there isn't one answer for all but remember the truth IS out there.

One final thing , the first 2 weeks of my pain were around the classic 9.04 hard lockup or freeze - I couldn't stay in Ubuntu for 5 mins without total freeze , usually it would happen within 2 mins - it was totally unusable !!
Its all caused by the sea change in 9.04 around the tickless machine/power management/clocking.

The answer ?.............


 (for me) three little commands on the kernel line in boot grub
NOAPIC  NOACPI HPET=DISABLE

I was so pleased to get this working that I didn't break down the line to see if it was the combination of all 3 or one of them that solved , though I know it wasn't the last command as by itself that didn't work.

So long and thanks for all the fish
Rubikon
[/SIZE]

---


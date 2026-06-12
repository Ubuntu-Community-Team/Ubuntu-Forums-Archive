---
title: "No sound after breezy install"
date: 2006-02-06
forum: Multimedia &amp; Video
---

### Post by bkrram on 2006-02-06
I just installed breezy on my laptop and most things worked fine except for the lack of sound. When I try to play a movie using Totem, no sound is heard even though the video plays fine.. I have a Sis card :

$cat /proc/asound/cards
0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with ALC250 at 0xe400, irq 18
bkrram@home-laptop:/etc/esound$ tail -2 /proc/asound/oss/sndstat
Mixers:
0: Realtek ALC250 rev 2

---

### Post by bkrram on 2006-02-07
I've managed to get the sound to come through on the headphones but still no luck getting it on the speaker.. Please help!!

---

### Post by wncben on 2006-02-08
Ubuntu noobie here:

Have been pouring through the forums, trying to  fix my own sound woes,  just a quick question:  Have you checked alsa mixer?  Ubuntu sets the volume to mute by default.  
  It sounds like you may have something muted or unmuted that is causing a problem. sometimes other channels can cause conflicts.  If you have any iec devices on the mixer board, mute them.  Try muting or unmuting the 'pc speaker'. 

Still new to this, but alsa seems to be the root of my sound woes.
~Ol' Ben

---


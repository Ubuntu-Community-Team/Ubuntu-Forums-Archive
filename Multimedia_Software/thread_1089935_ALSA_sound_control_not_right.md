---
title: "ALSA sound control not right"
date: 2009-03-07
forum: Multimedia Software
---

### Post by IceCap on 2009-03-07
This problems is on a Mythbuntu setup (which I believe is basically xubuntu) but I believe that the actual problem resides in how ALSA is setup (incorrectly).
  First the hardware:
[LIST]
[*]Intel Pentium 4 motherboard with Intel 82801DB-ICH4 integrated sound chip/system.
[*]PVR-350, sound out hooked to microphone plug on motherboard, sound-out on motherboard hooked to speakers
[/LIST]

  Watching TV or recordings I get sound, but I can't control it with my remote.  The OSD change sound information comes on the screen AND it is controlling the 'Master' or 'PCM' (depending on setup in MythTV) channels in the alsamixer (as observed in alsamixer through ssh from another machine), but neither the 'Master' nor the 'PCM' are controlling the sound.  Instead, when I play around with the alsamixer through ssh while MythTV is running, only the 'mic' (obviously) and the 'Headphon' channels control the volume (and mute).

  So it appears to my (untrained) eye that the issue is within how alsa is controlling my sound system/card.  I've searched for information on how to set alsa up correctly but by the look of it, one really needs to know what he is doing in order not to mess things up.  So I was wondering if someone could help me out with this.

  On a side note, using the "internal" DVD player in Mythbuntu (which I believe is the mplayer) to play DVDs I don't get any sound.  However, using xine instead, works fine (and remote controls the sound but I believe that sound control is internal to xine, but xine doesn't seem to work quite as well video wise).  I'm assuming/hoping that this issue is related to the alsa setup.

  Thanks

  IC

---

### Post by IceCap on 2009-03-09
I updated the ALSA package to 1.0.19 using the script in one of the threads but same issue.

  Would it be better to ask this question on some other forums?  I'm noticing that there are lots of post around here on sound issue, most of which go unanswered.

  Thanks

  IC

---

### Post by IceCap on 2009-03-11
Anyone?

---

### Post by IceCap on 2009-03-14
I solved it.  Turns out one can type in the name of the ALSA channel you want to use for controlling the volume.  So by using ALSA and typing in 'Headphone' instead of selecting 'Master' or 'PCM' works fine.

  IC

---


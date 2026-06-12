---
title: "Surround Sound on Audigy SB0090 (emu10k1)"
date: 2009-01-21
forum: Multimedia Software
---

### Post by Omnistegan on 2009-01-21
Hi there everybody.

I'm struggling to get my 5.1 surround working on my Audigy 1 soundcard. ALSA seems to working fine, the code:
```
speaker-test -Dplug:surround51 -c6 -l1 -twav 
```
plays the correct sounds through the correct speakers, but I cannot get any 5.1 audio to play over more than just the front stereo speakers nor can I get stereo audio to play over more than just the front stereo speakers.

I've searched and tried all the ~/.asoundrc modifications to no avail. I've also read a number of posts about [emu10k1] cards and the "wave surround" slider that might be able to help me, but I can't seem to find it anywhere.

Thanks in advance everybody.

---

### Post by Shazaam on 2009-01-21
Open terminal, type in...
```
alsamixer
```
Anything marked MM is muted. Highlight it/them and click your m key to unmute. Up/down arrow keys control volume/level.
Or, if all that shows there is a PulseAudio slider, right-click the speaker icon in your panel, go to "Open Volume Control". On the lower right of the window click "Preferences" and enable what you want.

---


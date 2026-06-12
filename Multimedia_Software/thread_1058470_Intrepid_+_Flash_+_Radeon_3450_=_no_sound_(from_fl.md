---
title: "Intrepid + Flash + Radeon 3450 = no sound (from flash).. anyone have it working?"
date: 2009-02-02
forum: Multimedia Software
---

### Post by zim2dive on 2009-02-02
Anyone able to get sound from Flash using Intrepid and HDMI audio on a Radeon 3450.

I've tried adding myself to the audio group, setting FIREFOX_DSP, playing with gstreamer and gnome sound prefs.. all set to point to ALSA.

Alsa is version 1.0.19.

Firefox 3.0.5, Flash 10.0.r15, also tried with Opera 9.6

I had sound working for Flash when I used my onboard nvidia 8200 IGP.

With the Radeon 3450 I have sound working from every other possible source (rhythmbox, Amarok, VLC, songbird, etc).. just not Flash.

I don;t think I have pulse working (and my new-to-Ubuntu impression is that I want to keep it that way).. but again, all OTHER sound sources play just fine and this worked using my IGP.

thanks for any info,
Mike

---

### Post by zim2dive on 2009-02-04
changing my .asoundrc to > defaults.pcm.device 3   (WORKS) somehow made everything happy. (vs.> pcm.!default {
type hw
card 0
device 3
}      (FAILS)

What a lovely audio system we have ;)

env vars FLASH_AUDIODEBUG and FLASH_FORCE_ALSA were also in the mix.

---


---
title: "Major crackling audio / sample rate issue"
date: 2012-11-30
forum: Multimedia Software
---

### Post by walkingbeard on 2012-11-30
[COLOR=Gray][COLOR=Black]The problem is solved by muting the Line fader in alsamixer. I don't know why that would be causing so much noise, but the problem is fixed.[/COLOR]

Hi everyone,

I've got an E-MU 1820 soundcard/breakout box interface. It has worked for several years without much bother, but recently, just after upgrading to 12.10, I have been getting this constant static crackle.

After much experimentation, I worked out that if I lowered the Front fader in alsamixer, audio kept going, and the crackle disappeared. But the trouble is, that when I got to the end of the song, the next song would play silently. Furthermore, the main pulseaudio volume in the system tray would have gone to zero. So I began to think it was a pulseaudio issue, with pulseaudio grabbing the Front fader, as well as the PCM Front fader, which actually controls audio volume and connecting them together. But when I uninstalled pulseaudio, the crackling remained, and I had the same problem.

Now I have worked out that I change the sample rate in alsamixer from 48k to 44.1k, the crackling disappears completely, with no fading needed. That would be fine, but then my audio plays at a lower pitch than it should.

Is there somewhere I can set the system (pulseaudio?) sample rate to 44.1k? Setting up this card in Windows, I have to set the card sample rate from E-MU's mixer, and then go and set the same rate for Windows.

Help would be much appreciated. I am sitting here in constant crackling.[/COLOR]

---


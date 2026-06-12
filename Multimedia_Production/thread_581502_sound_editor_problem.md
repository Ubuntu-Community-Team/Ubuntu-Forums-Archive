---
title: "sound editor problem"
date: 2007-10-19
forum: Multimedia Production
---

### Post by nnjond on 2007-10-19
Needed a Sound Editor, so have dloaded Audacity. Seems great but when i playback my Line-in sample, it is speeded up. I can't believe this is the default setting? Is there something wrong?

---

### Post by Technoviking on 2007-10-19
Moved to more appropriate area of the forums.

---

### Post by Stochastic on 2007-10-21
What probably has occurred is that between your recording and your playback, the project changed sample rates (it increased if you're sample sounds sped up).  Try switching the sample rate to a lower value.

---

### Post by mrowth on 2007-10-21
> **nnjond said:**
> Needed a Sound Editor, so have dloaded Audacity. Seems great but when i playback my Line-in sample, it is speeded up. I can't believe this is the default setting? Is there something wrong?

Part of the "Mixer" toolbar is a slider to the right of a button with a green "playback" triangle, tooltip says "Play-at-speed". Maybe you've moved it from the "1.00x" position?

Does the recording play correctly when you play it in another sound editor (like Rezound) or in one of the media players?

Maybe there's a problem with ALSA sample rates? I know I used to have problems with distorted recordings before I got meself an .asoundrc with rate conversion (as well as software mixing for playback and capturing).

---


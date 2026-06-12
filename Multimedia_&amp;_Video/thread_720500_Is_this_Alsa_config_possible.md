---
title: "Is this Alsa config possible?"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by unimatrix on 2008-03-10
I would like to do four things. I want to know if this is even possible by generating a correct .asoundrc file?

First let me just show my system's audio configuration.
The following is the output from *$ aplay -l | grep card*
```

card 0: Audigy2 [Audigy 4 PRO [SB0380]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
card 0: Audigy2 [Audigy 4 PRO [SB0380]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
card 0: Audigy2 [Audigy 4 PRO [SB0380]], device 3: emu10k1 [Multichannel Playback]
card 0: Audigy2 [Audigy 4 PRO [SB0380]], device 4: p16v [p16v]
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]

```

I would like to:
1. use Audigy4's _digital (S/PDIF) output as default output_
2. have the same stream on Audigy's _digital AND analog_ outputs.
3. always _hear the same thing on my Logitech USB Headset_ as i would on Audigy's outputs
4. be able to _play audio in multiple applications simultaneously_

Basically, to have the default audio device output stream to Audigy4's digital-out, analog-out and the Logitech USB Headset (and use more than one audio application at once).

Is what I'm asking for even possible? What would I have to put in the .asoundrc file?

---


---
title: "Audio player with library using alsa"
date: 2011-12-16
forum: Multimedia Software
---

### Post by Nordvind on 2011-12-16
I'm fed up with the crappy pulseaudio, is there a player with a library, that uses any nice sound driver, like ALSA? Would be nice, if it was a plugin-enabled as well.

Alternatively, I've heard around that there is a plugin for rhythmbox, that forces it to use alsa, though found no evidence of it.

---

### Post by BicyclerBoy on 2011-12-16
Clementine can be pointed directly at any alsa plug..& it plays 192KHz/24bit without downsampling..

So can use:
- alsa libsamplerate plug-in to up-sample everything to max for external AVR.
- alsa AC3 encoder plug-in for multi-channel (AVR with no HDA HDMI)
- alsa hw device for direct LPCM multi-channel (HDMI HDA)

Other programs can just output to default pulse..

Pulse-audio can be configured to do some of this but I have a hard time trusting it..

---

### Post by Nordvind on 2011-12-18
Thanks, used Clementine for like a day, and I can clearly say it's much more powerful than I expected. It's faster, with **lots of** options, and with a good interface (and hasn't crashed yet, not to speak about the latency of rhythmbox crashes). It outclasses rhythmbox in every parameter, I just wonder, why that garbage is still bundled in (*)ubuntu distros by default.

---


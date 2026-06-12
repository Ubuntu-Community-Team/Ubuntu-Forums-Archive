---
title: "Installed Rhythmbox and Pulse, but no sound."
date: 2009-11-15
forum: Multimedia Software
---

### Post by chris_andrew on 2009-11-15
Hi, all.

I've got the Xubuntu meta-package installed, and am using ALSA.  I like Rhythmbox, so just installed it and it pulled-in Pulse as a dependency.  Unfortunately, when I play music I can't hear it.  I'm assuming Pulse is pointing at my built-in soundcard, but my speakers are plugged into my preferred soundcard.

Anyone know how to remedy this?

I installed Pulse Device/ Volume chooser, but still no luck.  Any idea, I love Rhythmbox?

Cheers,

Chris.

---

### Post by VertexPusher on 2009-11-15
PulseAudio is not a dependency of Rhythmbox. It depends on gstreamer0.10-audiosink which can be _either_ gstreamer0.10-pulseaudio _or_ gstreamer0.10-alsa.

If you install gstreamer0.10-alsa and remove all the PulseAudio stuff again, you should be fine.

---

### Post by chris_andrew on 2009-11-15
Perfect, thank you! :-)

I have sound.  Now I just need to solve why I keep getting a prompt saying:

"Looking for ID3 tag demuxer plugin" (or something similar!

Chris.

---


---
title: "rhythmbox won't use correct audio device"
date: 2010-08-22
forum: Multimedia Software
---

### Post by squaregoldfish on 2010-08-22
I've been having fun with trying to get the spdif to work my audio device to work through ALSA, having banished PulseAudio. My device is a VIA 8237 which has the interesting property that all the outputs are on the same device, distinguished using sub-devices.

The standard stereo output is hw0,0,0 and the spdif output is hw0,0,3. I've set my default audio device in ~/.asoundrc as follows:

```
pcm.!default {
        type hw
        card 0
        device 0
        subdevice 3
}

```

This has worked for everything except Rhythmbox, which is still playing its music through the standard stereo output. I've checked gstreamer-properties and suchlike, and they're all set up correctly.

Can anyone give me any clues? Is Rhytmbox unable to figure out subdevices?

TIA,
Steve.

---


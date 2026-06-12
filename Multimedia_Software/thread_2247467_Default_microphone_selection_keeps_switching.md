---
title: "Default microphone selection keeps switching"
date: 2014-10-08
forum: Multimedia Software
---

### Post by Thee on 2014-10-08
Hi.

I have 2 audio inputs, one from my headset and other from my webcam.
Naturally, I want to use my headset's mic and not my webcam's mic because of better quality. So I don't really need the webcam mic, only the webcam video.
But when ever I set my default mic (headset) in Sound Settings, and then close the Sound Settings, it immediately resets my selection to the webcam mic.
And I can't get it to stick no matter what, it keeps changing from headset mic to webcam mic.

I tried to add the following lines to ~/.pulse/default.pa without any luck.

```

### Make some devices default
set-default-source alsa_input.pci-0000_00_14.2.analog-stereo
set-default-sink alsa_output.pci-0000_00_14.2.analog-stereo

```

Now, I need either a way to set my default mic permanently, or disable my webcam mic completely from showing up in the audio devices list (without disabling webcam video).
Both solutions would do. Using Ubuntu 14.04.

Help would be really appreciated, because this is getting really annoying...

---


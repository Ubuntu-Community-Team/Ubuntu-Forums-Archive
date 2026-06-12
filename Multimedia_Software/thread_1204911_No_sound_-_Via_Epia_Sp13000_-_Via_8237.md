---
title: "No sound - Via Epia Sp13000 - Via 8237"
date: 2009-07-05
forum: Multimedia Software
---

### Post by ThomThom on 2009-07-05
I just installed XUbuntu 9,04 on a Via Epia SP 13000
It has a Via8237 chipset

I've previously had XP and Ubuntu 8.04 installed. The Audio worked fine.
But I et no audio with XUbuntu when I try to play any audio files.

I don't have much experience with Linux.

There is an icon next to the clock which bring up a Mixer window.
From there I can choose from the drop down "VIA 8237 (Alsa Mixer)" or "VIA Technologies VIA1617A (OSS Mixer)"
It's currently set to the first.

I've clicked the "Select Controls..." button and made all the controls visible - looking for muted controls, but the few that's muted makes no difference when unmuted.

Anyone got any ideas to what it could be?
What do I need to check for?
How do I know everything is installed correctly?

Is there a Control Panel applet like in Windows?

---

### Post by ThomThom on 2009-07-05
Shouldn't there be a Sound icon in the Setting Manager? I got none.

---

### Post by ThomThom on 2009-07-05
Ok.
Got it working.
Not sure what did it, but I found that my user wasn't listed in the audio group.
And the VIA DXS volume settings where all set to 0 (not muted, but simply lowest volume level...)

Now I have it working fine. :)

---


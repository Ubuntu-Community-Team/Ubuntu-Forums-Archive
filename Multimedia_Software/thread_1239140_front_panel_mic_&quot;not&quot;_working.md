---
title: "front panel mic &quot;not&quot; working"
date: 2009-08-13
forum: Multimedia Software
---

### Post by Jst on 2009-08-13
Hi, I have a problem with getting to work the microphone plugged-in to the front panel jack of my computer.

I have an ASUS M4A78T-E motherboard, which uses a VIA VT1708S audio codec. I then have one jack for the microphone on the back of the computer (this one works fine) and one on the front, which mostly doesn't work.

Now if I volume up the front microphone slider for playback in the mixer it works nicely. The problem comes when i try recording something.

I tried changing the sound capture device in System/Preferences/Sound and here's what I get. First of, it's a mess there giving me so many options. I'll just go on and list all the options there and say what I get where.

```

HDA ATI SB VT1708S Analog (ALSA)
UCQ01000               Samsung UC Audio USB Audio (ALSA)
HDA ATI SB VT1708S Analog (OSS)
UCQ01000               Samsung UC Audio USB Audio (OSS)
HDA ATI HDMI OSS Control Device (OSS)
ALSA - Advanced Linux Sound Architecture
OSS - Open Sound System
PulseAudio Sound Server
Test Sound
Silence

```

Those two Samsung entries are from the monitor which has built-in a web-cam, microphones, and speakers. Now when I tested the back panel microphone jack the microphone worked fine. Confusingly it workes even when i have chosen the Samsung OSS device (which should be the microphone on the monitor, with Samsung ALSA everything is OK) and HDA ATI HDMI OSS (which I assume is for the HDMI port on the back panel). I doubt this has anything to do with my true problem but i felt saying it anyway.

Here are the results for trying the front panel microphone jack. HDA ALSA passes the first test if I pressed the test button before that on HDA OSS, UCQ OSS, HDA HDMI OSS, ALSA, PulseAudio and then not waited too long for testing it under HDA ALSA (can't wait more than a couple of seconds or else it wouldn't work). Then if I try the test again it would not work (actually if the first test is really short and i click the test button really fast again it would work; I can do this until those couple of seconds don't pass).
All the other devices give nothing apart from the OSS device which has again the same behavior as the HDA ALSA device.


Hope someone can help me, thanks.

---


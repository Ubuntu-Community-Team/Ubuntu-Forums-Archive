---
title: "NVidia CK8S Optical Playback Question"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by justinlindh on 2006-11-07
I had posted this seeking help in the "Comprehensive" thread, but I didn't get any responses after three days. Sorry for the cross post.

I'm running 6.10 Edgy final (with updates). I'm using the ALSA 1.2.10 output plugin. The following are my settings:

Audio Device: hw: 0,2 (NVidia CK8S: NVidia CK8S - IEC958)
Mixer card: NVidia CK8S
Mixer device: IEC958 Playback AC97-SPSA

I was finally able to get sound to play in a couple of applications by setting the Devices to use IEC958 in Sound Preferences, which I assume is my optical audio out, but there doesn't appear to be any "system" sounds (such as login, sound from flash in browsers, etc).

The IEC958 isn't listed in the "Sounds" tab (where the samples for sounds such as the login/logout etc are). Only the NVidia CK8S and MPU-401 UART are listed (neither of which work when testing them).

Is this a bug, or am I missing something in the configuration? Any help is greatly appreciated.

Bonus question: How do I stop the monitor from turning off while I'm using Totem Media Player? I changed the preferences to "Never" turn off in Power Management, but it doesn't seem to care.

---


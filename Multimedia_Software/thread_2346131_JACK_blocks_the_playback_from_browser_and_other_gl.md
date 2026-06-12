---
title: "JACK blocks the playback from browser and other gliches"
date: 2016-12-11
forum: Multimedia Software
---

### Post by Sidrabs on 2016-12-11
I am testing certain connection setups with JACK, and I use the QjackCtl application to setup JACK and start/stop the JACK server. I am using Ubuntu 14.04 LTS.

I am not well acquainted with all things JACK, so I might be overlooking something obvious here, but please help me understand what's happening:

- With the JACK server started, browser (Chrome, YouTube) suddenly complains it can not start playback ("if playback doesn't begin shortly try restarting your device"). Once I stop the JACK server, the playback immediately starts
- The sound settings (particularly, Output panel) lets me choose a device for sound output and then lets me adjust settings for the selected device. Once the JACK server is started, those sound settings start glitching - changing the output device does not update the settings (more specifically, the Profile dropdown).

Should I register the applications, such as web browser, with the JACK server, to enable the playback? Or, perhaps I am not setting up the JACK properly? Currently those are almost default settings: Realtime checked, Driver alsa, Interface "hw:1,0":
[IMG]https://drive.google.com/uc?export=view&id=0Bz3CKML97e3XRjJyV3ZNLUhiQWc[/IMG]

---

### Post by marseille2 on 2016-12-12
You need install > pulseaudio-module-jack < if you're going to use pulseaudio with turn Jackd on and try to browse the web. Pulseaudio and Jackd can't talk to each other without the modules installed ... look for it in your package manager.

---


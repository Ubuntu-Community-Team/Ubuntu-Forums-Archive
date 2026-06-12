---
title: "Getting sound input with new alsa package, now Chrome trouble"
date: 2010-10-17
forum: Multimedia Software
---

### Post by meditatingfrog on 2010-10-17
So, i wanted to get sound recording working with my sound card, and to do this i first tried downloading and compiling new alsa from this site:  [http://monespaceperso.org/blog-en/2010/04/17/upgrade-alsa-1-0-23-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2010/04/17/upgrade-alsa-1-0-23-on-ubuntu-karmic-koala-9-10/).  this actually got me the ability to record (and no, the problem before this wasn't that the sound input was muted).  anyway, now i have another problem, after getting the built in microphone working, chrome doesn't like to play nice with totem.  i have surmised this is caused by chrome not choosing the alsa pulse plugin.  but so far, everything i've tried won't fix this, which includes:

this guide:  [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup) (which included updating the ~/.asoundrc file)
this guide:  [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
and this guide:  [https://wiki.ubuntu.com/Audio/UpgradingAlsa](https://wiki.ubuntu.com/Audio/UpgradingAlsa) (to upgrade the recommended method, instead of compiling alsa from source).  

so, i now have alsa 1.0.22.1.  and pulseaudio ver 0.9.19 (which i think is what came with karmic).  chrome/firefox/chromium intermittently doesn't want to share the audio hardware with gstreamer apps (totem/rhythmbox).  i can work around them not wanting to play nice (when they don't want to) by shutting down sound apps in chrome, and restarting pulseaudio, but if pulseaudio is accessing sound hardware (via gstreamer apps) chrome won't be able to play audio.  

any ideas are welcome.

---


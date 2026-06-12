---
title: "Missing audio output after using gnome sound-recorder"
date: 2012-06-14
forum: Multimedia Software
---

### Post by Todd in Berlin on 2012-06-14
I used Gnome Sound Recorder 2.32.0 and somehow turned off the audio input. Then I re-configured the audio in Sound Preferences but have not been able to get the audio output to work. The hardware is visible in Sound Preferences and the input audio does work now (confirmed by visual signal level in Skype.). Nothing is muted. I tried re-installing Sound Recorder but it did not help. Is there something I can do in Synaptic Package Manager which can help?

---

### Post by Todd in Berlin on 2012-06-14
Someone at Launchpad told me:

killall pulseaudio; rm -r ~/.pulse*

Wait 10 seconds, reboot

PROBLEM SOLVED!

---


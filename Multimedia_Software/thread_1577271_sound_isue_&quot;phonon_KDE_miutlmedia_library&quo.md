---
title: "sound isue &quot;phonon KDE miutlmedia library&quot;"
date: 2010-09-18
forum: Multimedia Software
---

### Post by Ka Fish on 2010-09-18
I get a quick pop up when I open digiKam. "Phonon: Multimedia Library, the audio playback device SIS SI7012 with ALC655 (SIS SI7012) does not work. Falling back to play/record threw the PulseAudio sound server." My Chromium web browser won't pick up certain alert sounds from some web sights, yahoo, fubar, facebook. Seamonkey is playing the sounds. I also have a Totem Browser Plugin 2.30.2  using GStreamer 0.10.28 that can't find the server in fubar.com/lounge. I'm truly hoping these issues are related & easy to fix.

---

### Post by solar george on 2010-09-18
I don't think they are related, the Phonon one is because Phonon tries to access the sound hardware directly but this fails when running with pulse audio (which is used with Gnome in Ubuntu) so only then does it try to use pulse audio as a fallback. If that annoys you you can install the KDE SC's [systemsettings]("apt://systemsettings") and change phonon to use pulseaudio as it's first preference.

---

### Post by Ka Fish on 2010-09-18
Thanks. Any idea why Totem Browser Plugin 2.30.2  using GStreamer 0.10.28 that can't find the server in fubar lounge?

---

### Post by solar george on 2010-09-19
I'm afraid I can't help there - I'm using Kubuntu so I don't use totem.
My only suggestion might be to install the VLC plugin and disable the totem one incase that helps.

---


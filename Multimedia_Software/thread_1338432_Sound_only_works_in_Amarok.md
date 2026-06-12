---
title: "Sound only works in Amarok"
date: 2009-11-26
forum: Multimedia Software
---

### Post by detyabozhye on 2009-11-26
For some reason, yesterday my sound just stopped working at random. Now the only application that makes any sound is Amarok; all other apps (Mplayer, Flash, etc.) silently fail. As soon as I log into my account on startup, I can open something in Audacity and the sound device is there and it will work, but at any time after that, the correct output device is missing from the settings list.

I'm running Kubuntu 9.10/KDE 4.3 on a Dell E1505 with an Intel sound card. In system settings I have the analog output as the preferred output device. Phonon is using the xine backend.

I solved the same problem in Kubuntu 9.04 by using PulseAudio as my preferred output, but PulseAudio doesn't work in 9.10 for me and it falls back to the analog output which silently fails.

---


---
title: "No sound in Gnome apps, but KDE apps work fine!"
date: 2010-03-08
forum: Multimedia Software
---

### Post by dbsoundman on 2010-03-08
I have a really strange issue here...

I'm on a system running Ubuntu 9.10 (gnome), upgraded from 9.04. I had some issues with pulseaudio early on so I managed to disable it and run alsa instead. After some update many moons ago, I noticed that applications like Firefox and Totem no longer played sound. In fact, when I start Totem, the volume control icon is blanked out, so it's not even clickable. Also, when I go to System>Preferences>Sound, I get a message saying "waiting for sound system to respond", which it never does.

However, throughout all of this, I have been able to play audio through Amarok with no issues. Initially I thought the issue was the fact that I had 2 soundcards (one for recording), so I removed the other one, and reinstalled the alsa packages, but still no dice. I finally realized today that it appears that all my KDE applications work fine with sound, but Gnome applications do not. This is even true for Virtualbox, which always gives me a message that the sound device is not reachable or something like that.

Can anyone give some suggestions on how to fix this issue? I did a search and found numerous threads on the web about issues with sound not working in KDE, but not the other way around. Also note that I do not have KDE installed on this computer, only Gnome with some KDE applications like Amarok (and the appropriate KDE backends to make them work of course).

Thanks,
Dan

---


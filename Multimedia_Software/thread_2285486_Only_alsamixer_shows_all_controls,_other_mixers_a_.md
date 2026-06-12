---
title: "Only alsamixer shows all controls, other mixers a limited set only"
date: 2015-07-06
forum: Multimedia Software
---

### Post by Petr_Be on 2015-07-06
Hello.

I use Ubuntu MATE 14.04 with an external USB 7.1 sound card (C-Media CM6206 chipset).

I have limited knowledge of pulseaudio, as it didn't exist back when I was doing some serious audio stuff on Linux for the last time many years ago (it was in times of switching from OSS to ALSA), so please excuse me if I'm asking in a stupid way:).

Sound works fine but the problem is that a full set of volume controls for all the channels is only available in alsamixer, which has to be launched from terminal.
This is an issue for non-advanced users. (I'm not the only user of the computer.)

I tried several GUI mixers.
Either they show only master volume and capture, this is the case with alsamixergui and qasmixer - probably because they can't deal very well with pulseaudio.
Or they show some more controls but still a very limited set compared to alsamixer in console - this is the case with kmix, xfce4-mixer and pavucontrol.

Is there a way to show all the volume controls available in alsamixer in a GUI mixer?

I guess disabling pulseaudio would help, but AFAIK it's required for the volume control icon in MATE panel to work properly.

Thank you very much for any hint.

Petr B&#345;e&#328;

---

### Post by Yellow Pasque on 2015-07-06
alsamixergui doesn't offer the option to switch devices after you start it, so you have to get the correct device when you start it. Try:
```
alsamixergui -c 1
```
If that doesn't work, look at aplay to figure out what number the USB card is:
```
aplay -l
```
I don't really see any advantage to using alsamixergui vs. running alsamixer in a terminal windows.

```
AFAIK it's required for the volume control icon in MATE panel to work properly.
```
You can install mate-media-gstreamer and mate-settings-daemon-gstreamer packages to work around that. Of course, if you remove pulse, other programs may not function correctly. Not recommended...

---


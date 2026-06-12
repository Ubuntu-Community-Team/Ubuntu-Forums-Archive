---
title: "Pulse Audio and Flash: My Fix"
date: 2009-08-13
forum: Multimedia Software
---

### Post by Strongmind on 2009-08-13
After a while, I finally got pulse audio to play nice with flash. This fix also works with Wine. I decided to share my fix with everyone.

Before installing pulse audio, install asoundconf-gtk. If PulseAudio is already on your computer, purge it and delete your ~/.asoundrc file. Then reboot.

```
sudo apt-get purge pulseaudio
```

```
sudo apt-get install asoundconf-gtk
```

You should now be able to type asoundconf-gtk in a terminal or go into System -> Preferences -> Default Sound Card. Obviously, this lets you change the default sound card for Alsa. One of the choices is PulseAudio.

Time to install pulseaudio and some graphical tools.

```
sudo apt-get install pulseaudio pavucontrol pavumeter paman padevchooser paprefs
```Change your default sound card to PulseAudio and try it out!:)

---

### Post by mlalevic on 2009-09-15
Thanks mate! worked like a charm :)

Btw, the last step is unnecessary since installing asoundconf-gtk installs all the rest.
Oh yes, that's Ubuntu 9.04 with Flash version 10.0 r32

---


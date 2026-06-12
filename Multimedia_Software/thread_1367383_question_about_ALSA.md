---
title: "question about ALSA"
date: 2009-12-29
forum: Multimedia Software
---

### Post by kwbauson on 2009-12-29
OK, when I first installed ubuntu, none of  the sound was working. Then I installed ALSA. As far as I can figure, ALSA is the way I can get any audio, but I don't know how to set it as the default sound system. Is there a way to do this? Right now, I only can get audio if I go into the sound preferences of a program (if they exist) and tell it to use ALSA.
Thanks!

---

### Post by VertexPusher on 2009-12-29
First make sure that the following packages are installed:

gstreamer0.10-alsa
gnome-alsamixer

Then remove the following packages:

gstreamer0.10-pulseaudio
vlc-plugin-pulse
pulseaudio

Log out and log in again. Now all your applications will use ALSA instead of PulseAudio.

---


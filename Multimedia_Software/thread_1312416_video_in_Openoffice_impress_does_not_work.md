---
title: "video in Openoffice impress does not work"
date: 2009-11-03
forum: Multimedia Software
---

### Post by jurgen32 on 2009-11-03
Hello.

I'm working with Kubuntu Karmic 64b.
Current openoffice version is 3.1.1.

Everytime when I insert a video in the presentation and try to rezize it or even play openoffice freezes. When this happens I get a extern 'mplayerlike' window which shows the start of the video but it's not playing.
I earlyer versions this was never a problem.
I installed all advised codecs but still no proper embedded video.
I did a fresh install of my whole system but this didn't make any differents.

I hope somebody can help me.

Jurgen

---

### Post by jurgen32 on 2009-11-10
I think I solved the problem with installing the package: gnome-media
This package will install the following packages:
gnome-media-common
gstreamer0.10-pulsaudio
libcanberra-gtk0
libcanberra-gtk-module
libgnome-media0
libpulse-browse0
libpulse-mainloop-glib0
libspeexdsp1
libunique-1.0-0
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-udev
pulseaudio-module-x11
pulseaudio-utils

Which of these packages brought the solution??? I really don't know, but if you know I'm still interested.

bye,
Jurgen

---


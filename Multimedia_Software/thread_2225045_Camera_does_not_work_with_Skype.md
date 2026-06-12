---
title: "Camera does not work with Skype"
date: 2014-05-19
forum: Multimedia Software
---

### Post by groundnut on 2014-05-19
sudo gedit /usr/share/applications/skype.desktop

I have to combine two commands in the skype.desktop file above.
namely:
Exec=bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'
and
Exec=env PULSE_LATENCY_MSEC=60 skype %U

How do I combine these to commands so I can change the skype.desktop file?

---


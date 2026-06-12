---
title: "Have no sound, help"
date: 2011-06-30
forum: Multimedia Software
---

### Post by dvded on 2011-06-30
Was working on 10.4 out the box

Soundcard is internal - Intel.

[http://www.alsa-project.org/db/?f=c12d21b72ac108413cf1cfe80a9f91752b5c579c](http://www.alsa-project.org/db/?f=c12d21b72ac108413cf1cfe80a9f91752b5c579c)

Removed pulse, not helped.

---

### Post by lidex on 2011-06-30
> **dvded said:**
> Was working on 10.4 out the box

Soundcard is internal - Intel.

[http://www.alsa-project.org/db/?f=c12d21b72ac108413cf1cfe80a9f91752b5c579c](http://www.alsa-project.org/db/?f=c12d21b72ac108413cf1cfe80a9f91752b5c579c)

[COLOR="Red"]Removed pulse, not helped.[/COLOR]

Did you think it would?
For troubleshooting purposes please return to default settings and run the alsa-info script again. Remove your model switch from alsa-base.conf:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
delete this line, save, close:
```
options snd-hda-intel model=basic
```
Now re-install pulseaudio:
```
sudo apt-get install pulseaudio gstreamer0.10-pulseaudio
```
Reboot.

---


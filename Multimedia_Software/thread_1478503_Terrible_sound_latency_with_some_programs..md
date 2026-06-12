---
title: "Terrible sound latency with some programs."
date: 2010-05-09
forum: Multimedia Software
---

### Post by Rydian Morrison on 2010-05-09
I've got terrible sound latency (about one second between actions and sound) in some programs.

Flash in both firefox and chrome (including youtube videos) and ZSNES (SNES emulator) are two offenders, as is Audacity.
Videos played in the default "movie player" and VLC play with no delay, though.

It's an eMachines T2899 desktop, FIC AU31 motherboard, nForce2 chipset, AC97 sound (integrated), running Xubuntu 10.04 (fresh wubi install as of a few days ago), 2.6.32-22.

I've been told it could be an issue with the ALSA buffer size, or pulseaudio introducing latency... but I've no clue how to go about fixing it.

[(LSPCI output)]("http://paste2.org/p/820145")
[(LSPCI verbose output)]("http://paste2.org/p/820158")
[(Aplay output)]("http://paste2.org/p/820153")

As a note, I'm not very familiar with linux yet, but I will try to gather any information you need.


EDIT: Upon using the SNES9X emulator (which allows for choice of sound system)...
[color=red]Portaudio causes laggy emulation and bad sound latency.[/color]
[color=green]Open Sound System plays fine.[/color]
[color=red]SDL causes laggy emulation and bad sound latency.[/color]
[color=green]ALSA plays fine.[/color]
[color=green]Pulse Audio plays fine.[/color]


EDIT2: Changed the title.  The original was "Terrible sound latency with some programs.", which probably lead people to think this had to do with using ubuntu as a recording studio, and to skip over it. ^^;


EDIT3: "sudo apt-get remove --purge pulseaudio" did nothing, so I reinstalled it just in case.


**EDIT4:** Upon running the following commands, the issue seems *partially* fixed.

```
sudo apt-get purge libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev   pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol 

sudo apt-get install gnome-alsamixer alsa-oss python-alsaaudio
```I can now play stepmania and youtube videos with only a slight amount of latency (a tolerable amount for now).

Furthermore upon testing ZSNES, it has zero latency... until I fast-forward, then the latency returns.  Going into and then out of the GUI returns the latency to 0.

Upon trying SNES9X...
[COLOR=green]Portaudio now plays fine.[/COLOR]
[COLOR=green]Open Sound System still plays fine.[/COLOR]
[COLOR=#999900]SDL now causes intermittent emulation lag, though it's not totally unusable like before.[/COLOR]
[COLOR=#999900]ALSA no longer plays fine, there's intermittent stuttering.[/COLOR]
Pulse Audio plays no sound at all, of course.

There's also annoying/random popping in audio I'd like fixed as well. :(

---

### Post by Rydian Morrison on 2010-05-11
This thread is multiple pages back, so... bump?

---

### Post by Rydian Morrison on 2010-05-11
Bump again.

---

### Post by Rydian Morrison on 2010-05-11
Again, bump.

---

### Post by Rydian Morrison on 2010-05-12
Bump. :(

---

### Post by Rydian Morrison on 2010-05-13
Bump.

---

### Post by Rydian Morrison on 2010-05-13
Bump. :(

---

### Post by Rydian Morrison on 2010-05-13
Bump.

---

### Post by Rydian Morrison on 2010-05-14
Bump. T_T

---

### Post by Rydian Morrison on 2010-05-15
Bump.

---

### Post by Rydian Morrison on 2010-05-15
Bump. :(

---

### Post by Rydian Morrison on 2010-05-15
Bump.

---

### Post by Rydian Morrison on 2010-05-16
Bump.

---

### Post by Rydian Morrison on 2010-05-16
Bump.

---

### Post by The_Eddster on 2010-06-04
bump

---

### Post by AbsolutelyRidiculous on 2010-08-25
Bump. This topic needs to be solved.

---


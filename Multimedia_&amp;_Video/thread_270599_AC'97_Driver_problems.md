---
title: "AC'97 Driver problems"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by Izuil on 2006-10-03
Okay so i've had problems getting sound working in 2 applications at the same time so i thought that it might help to install AC'97s own driver... Yeah right...
Anyways When the installation seems to be finishing it gives me ```
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
install: line 102: alsaconf: command not found

```
and now when i try to run alsamixer it gives me:```
alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB,
version ALSA_0.9 not defined in file libasound.so.2 with link time reference
```

What's my problem?

EDITED
Which curses library?

---

### Post by Izuil on 2006-10-04
Solved it.

---


---
title: "OSS sound for the desktop?"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by eracerbit on 2007-05-14
edit: long story short, i'm trying to wrap oss with esd. is this possible?


I am setting up an ancient Compaq Presario 1260 (64 mb ram) with an old soundblaster card that refuses to work with alsa. However, OSS sb module gets sound out of the card; i can load it like this:

```
 modprobe sb io=0x220 irq=5 dma=1 dma16=5 
```

Testing this with moc (mocp) produces sound.

Now, i want to be able to use this configured sound for the entire system, or at least gnome-games. gnome-games seem to expect esd. tried to load esd like this:

```
 esd -d /dev/dsp 
```

...but esd complains that there is no PCM at /dev/dsp. /dev/dsp exists.

Thanks in advance to anyone who can offer a solution for my problem =)

*edit -- for the record: instead of running gnome (too slow for this machine), i'm running a minimal xsession with just lxsession, lxpanel, openbox, and pcmanfm.*

---

### Post by eracerbit on 2007-05-15
bump...

---


---
title: "Gnome audio problem"
date: 2008-11-07
forum: Multimedia Software
---

### Post by Borbus on 2008-11-07
I have just upgraded to Ubuntu 8.10. Now audio does not work with gnome apps (rhythmbox, totem etc.) In gnome-sound-properties I select ALSA and when I press test I get: Could not open audio device for playback.

My card is an M-Audio 1010LT. I know that the driver is installed and working because VLC Player works absolutely fine and I also hear the sound on the login screen.

This one has me completely confused, VLC Player (and gdm) works, Gnome does not... Any ideas?

Thanks.

Edit: more info that might be useful, VLC gives this error:  alsa audio output error: unable to commit hardware configuration (Input/output error), but it plays anyway.

---

### Post by Borbus on 2008-11-08
I removed pulseaudio to get it working following this thread: [http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

There is also a work around to get pulseaudio to work with the 1010LT but I couldn't be bothered to do it. The workaround: [https://tango.0pointer.de/pipermail/pulseaudio-discuss/2008-January/001240.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2008-January/001240.html)

---

### Post by 73ckn797 on 2008-11-08
Did you set volume levels? Double click on speaker icon and you can set all levels from there. Recommend running all levels to max. I did on my laptop cause speaker volume was very low after fresh install of 8.10.

---

### Post by jamoo1980 on 2009-02-09
> **73ckn797 said:**
> Did you set volume levels? Double click on speaker icon and you can set all levels from there. Recommend running all levels to max. I did on my laptop cause speaker volume was very low after fresh install of 8.10.

...I had a similar problem with apparently no sound after re-installing the Gnome desktop. It turned out that the sound levels had been muted. When I un-muted them, by double clicking on the speaker icon as described above, everything returned to normal.

---


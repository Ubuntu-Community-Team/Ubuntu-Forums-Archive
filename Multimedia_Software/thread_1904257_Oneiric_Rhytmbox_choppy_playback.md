---
title: "Oneiric Rhytmbox choppy playback"
date: 2012-01-04
forum: Multimedia Software
---

### Post by nacho-wan on 2012-01-04
I have a couple of hours researching this problem, but I haven't found any concrete information around so I'm turning to the forums.

After some trouble with my partitions, yesterday I was able to install Oneiric Oncelot on my 2009 Dell Inspiron 1525. The installation is on a separate partition, as well as the home directory that has been inherited for several ubuntu versions.

My current problem is choppy playback in rhythmbox. I load the application at startup and any time I open another app like chromium, the music stops and repeats a couple of seconds of audio like an old scratched disc.

Looking through the system log, I got these creepy messages: 

```
[alsa-sink] alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: -1865240 bytes (-10573 ms).
Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
```

```
ALSA woke us up to write new data to the device, but there was actually nothing to write!
Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
```

```
rhythmbox-metad[4675]: segfault at 365abc26 ip 002287f0 sp bff70230 error 4 in libgobject-2.0.so.0.3000.0[1f6000+4d000]
```

Maybe somebody here can give me some advice on how to proceed in this matter?

---

### Post by nacho-wan on 2012-08-21
I managed to solve my issue by enabling the "crossfade between tracks" in preferences / playback menu. That did the trick.

---


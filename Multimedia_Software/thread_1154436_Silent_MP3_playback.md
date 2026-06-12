---
title: "Silent MP3 playback"
date: 2009-05-09
forum: Multimedia Software
---

### Post by woody.cool on 2009-05-09
Hi,
Apologies if this has been done before.

I've recently installed Ubuntu 9.04 (32-bit) and I'm really struggling.
No matter what I try (and what packages I install to get the MP3 codec), playback doesn't work

It looks like it's playing back the MP3 (no error messages) and I even get visualizations in Rhythmbox, buy no sound from MP3s

I know my sound card is working, as I get all the Ubuntu system sounds.

Has anybody got any ideas?

P.S. I'm a total linux noob, so I'm not overly familiar with some things. Any help is appreciated.

---

### Post by HavocXphere on 2009-05-09
Chances are that the sound is going to the wrong device/sound  output.

The following thread has helped me with sound issues, perhaps it will help you too.

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by woody.cool on 2009-05-09
> **HavocXphere said:**
> [http://ubuntuforums.or/showthread.php?t=1130384]("http://ubuntuforums.org/showthread.php?t=1130384")

Thanks HavocXphere.
Although this thread didn't help me out on it's own, it did contain links to other threads etc.
Turned out, I needed to add
**options sda-hda-intel model=5stack** to some ALSA configuration file (can't remember the filename of it now)

So now, I'm sitting back, listening to some tunes \\:D/

EDIT: I restarted (to check that it's gonna work) and I'm back to square one ](*,)

---


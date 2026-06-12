---
title: "VLC - sound stutters"
date: 2008-04-30
forum: Multimedia Software
---

### Post by violinmandan on 2008-04-30
I'm having problems with VLC in Ubuntu 8.04. It “stutters” every few seconds during sound playback.
This has not been a problem until recently, and I don't know what caused it.
At first, I thought it was a GNOME issue, because Amarok and StepMania were unaffected; however, I tried it with Audacity (It's GNOME, right?), and it worked fine.

Any ideas?

---

### Post by starvingartist on 2008-05-01
I have the exact same problem (probably). No playback problems with Gutsy & XMMS. Updated to Hardy yesterday, installed several audio players to find something I like. All played music without any jitter. The only one that I like, VLC, does however jitter badly. :( Any help (n00b-level, if possible) is appreciated.

---

### Post by starvingartist on 2008-05-01
I see this was already answered:
[http://ubuntuforums.org/showthread.php?p=4850437#post4850437](http://ubuntuforums.org/showthread.php?p=4850437#post4850437)

Switching everything from autodetect to ALSA worked great.

---

### Post by zagibu on 2008-05-01
I have the same problem with vlc. I tried reverting back to Alsa, or OSS, but it doesn't change anything. Totem doesn't have the stuttering, btw.

---

### Post by mivo on 2008-05-01
Okay, here is how to fix it:

In *System -> Preferences -> Sound*, change everything to ALSA. Then start VLC and go to *Settings -> Preferences -> Audio* and check "Advanced Options" (right lower corner). Then choose "ALSA audio output".

That fixes the stuttering. If you have a problem with sound only working for one application at a time, download the **alsa-oss** package and add aoss before the command in the appropriate application launcher.

---

### Post by Pendragoon99 on 2008-07-25
thanks for the tip , solved my vlc sound and stability problems

---


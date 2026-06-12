---
title: "vlc stopped working after update"
date: 2009-05-06
forum: Multimedia Software
---

### Post by Arndt on 2009-05-06
I'm using Intrepid. (I'd like to report the correct version number, like 8.04 or 8.10, but how do I determine it?)

I have been using vlc to play web radio. When update notifications for Ubuntu appear, I usually perform them, without noting carefully what is being updated - it's often a lot. Today (possible yesterday, I've been away) there was one update, a library of some sort (does a log exist if what updates have been made?), and now vlc won't play anything, it just sits there, silent.

The last few lines of output when I start it from the command line are:

> [00000438] access_mms access: selecting stream[0x1] audio (94 kb/s)
[00000438] access_mms access: connection successful
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
[00000476] oss audio output error: cannot open audio device (/dev/dsp)


Does anyone recognize this? What can I do to fix it?

---

### Post by Bigneil on 2009-05-06
you could just try removing VLC then re-intalling it?   it's worth a try!

---

### Post by Arndt on 2009-05-06
> **Bigneil said:**
> you could just try removing VLC then re-intalling it?   it's worth a try!

I could, but I suspect that won't fix it, since amarok and aaxine/fbxine also have problems.

---

### Post by Arndt on 2009-05-06
> **Arndt said:**
> I could, but I suspect that won't fix it, since amarok and aaxine/fbxine also have problems.

Rebooting solved the problem.

---

### Post by Arndt on 2009-05-07
> **Arndt said:**
> Rebooting solved the problem.

It did just then, but the problem has reappeared. Something else might be hogging the sound card, but "lsof /dev/dsp" doesn't show anything. Quitting Firefox and then trying to use vlc also doesn't succeed.

---

### Post by Arndt on 2009-05-11
> **Arndt said:**
> It did just then, but the problem has reappeared. Something else might be hogging the sound card, but "lsof /dev/dsp" doesn't show anything. Quitting Firefox and then trying to use vlc also doesn't succeed.

bump

---

### Post by caitifty on 2011-02-25
In 10.04, I found the permissions for /dev/dsp were screwed up after an upgrade so many programs (including vlc and mplayer) gave 'audio output error: cannot open audio device (/dev/dsp)' errors & no sound.

Solution for me was:

sudo chmod 666 /dev/dsp

Hope this helps someone.

---


---
title: "Sound works at first, but keeps dropping connection"
date: 2010-05-16
forum: Multimedia Software
---

### Post by CountryFan on 2010-05-16
I've installed Lucid Lynx in both kubuntu and xubuntu variants, and experienced the same problem, (Note I'm also still running 9,04,on the same computer, trouble free)

With 10.04, the problem is that sound playback software works initially, but drops the connection with the sound driver randomly, at times varying from a few seconds to a couple of minutes. It seems to happen regardless of whether Alsa or PulseAudio is set as default. 

This happens with Movie Player, VLC, Audacity, and with Flash in Firefox - they all appear to start normally, with sound, but soon fail. (Again, I don't have this problem with earlier releases, using the same computer) I know little about sound configuration, and would be grateful for any help.

---

### Post by CountryFan on 2010-05-16
"Movie Player" is giving an error message like this:

*pa_stream_writable_size() failed connection terminated*

(I'm afraid that means nothing at all to me - does anyone recognize it, and know how to deal with it?)

---

### Post by CountryFan on 2010-05-16
I've discovered that I can run Audacity for much longer (up to about 40 minutes) if I set the project rate well below the default value of 44100 hz.
However, that is not a solution: it doesn't eliminate dropping the connection (only makes it rarer) - and it doesn't help the other applications.

I wondered if I might have a corrupt installation - but if so, I don't see how it would happen in both kubuntu and xubuntu (which were downloaded on different days from different mirrors)

I still have a working installation of Jaunty on another partition, which doesn't have this problem

---

### Post by arindrel on 2010-05-17
I Have the same problem .. same error messages .. also very high CPU usage of Pulsaudio ... 

was a solution ever found to this issue or is it just reinstall and hope?

---

### Post by CountryFan on 2010-05-17
I've tried all I can think of. (These are fresh installations, not upgrades)

It doesn't seem to be a hardware problem, as Jaunty works with the same soundcard.
I don't think it's a mixer settings problem, since sound works at first, for a variable time.
In case it was a driver problem, I followed the steps explained by LordRaidon in the sticky guide for this forum - purging Alsa and getting it from a fresh kernel; and then re-compiling the Alsa driver for my card. I'm afraid that made no difference.

I'm about out of ideas - and it looks as if I'll have to stick with Jaunty

---

### Post by chrisinspace on 2010-05-31
I'm having the same issue.  The sound works fine for a while, but then when the system gets taxed out, it drops the sound.  Restart the app and the sound works fine again for a while.  Seems like a similar situation at [this post]("http://ubuntuforums.org/showthread.php?t=1484569"), too.

---


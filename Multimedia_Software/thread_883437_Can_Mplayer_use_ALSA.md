---
title: "Can Mplayer use ALSA?"
date: 2008-08-07
forum: Multimedia Software
---

### Post by Comandos on 2008-08-07
Hey,
I recently discovered Mplayer and liked it a lot. The problem was, that it seemed to want to use Pulse Audio, which my Skype hates. Now, I'd like them to coexist but can't get the solutions posted online to work for me. Is there a way to get Mplayer to just use ALSA?

---

### Post by ibutho on 2008-08-07
Yes, Mplayer can use ALSA. Look at the MPlayer options/preferences and I am sure there is an option there to change the audio settings to use alsa.

---

### Post by mc4man on 2008-08-07
For the gui version (gmplayer) r. click in gui -> preferences -> audio and pick alsa from list (just click on it)
from cli use -ao alsa

---

### Post by markbuntu on 2008-08-08
If you want to get your skype working with pulseaudio, there is a fix here:

[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

---


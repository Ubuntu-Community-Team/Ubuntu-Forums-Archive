---
title: "mpd &quot;error opening audio device&quot;"
date: 2009-12-22
forum: Multimedia Software
---

### Post by bobdobbs on 2009-12-22
Hi.

Mpd randomly stopped working.

I use gmpc to run mpd. Today when I booted, gmpc briefly displayed "error opening audio device". The tracks still show as playing, but I get no sound.

Afaik, the permissions are correct and the pulse settings are correct: I've mostly been getting sound until now.

How can I fix this ?

---

### Post by bobdobbs on 2009-12-22
> **bobdobbs said:**
> Hi.

Mpd randomly stopped working.

I use gmpc to run mpd. Today when I booted, gmpc briefly displayed "error opening audio device". The tracks still show as playing, but I get no sound.

Afaik, the permissions are correct and the pulse settings are correct: I've mostly been getting sound until now.

How can I fix this ?

Solved:

I went to my sound preferences by right-clicking the volume icon.
Under the tab "output", there are two options.
I switched from the selected option to the unselected option:
"Internal Audio Analog Stereo".

This restored sound.

---


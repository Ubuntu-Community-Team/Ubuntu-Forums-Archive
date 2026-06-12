---
title: "[SOLVED] Cannot hear sound from audio capture"
date: 2008-07-28
forum: Multimedia Software
---

### Post by johann_p on 2008-07-28
I am using Gutsy on Intel 32 with all updates installed.
After some trial and error (and de-installing Jack) i managed that i can record sound with audacity from line in/mic.
However, the sound I am recording is not played on the speakers, although I hear it when I play the recored track.
In the volume control, the Capture bars have to symbols undernath: a speaker and a mic. None of the two are crossed out.

So I would have assumed that this means that the captured sound is being "monitored", i.e played live on the speakers, but this is not the case.

How can I achieve that line out is played live?

---

### Post by johann_p on 2008-07-28
Could somebody please explain when I should hear the signal that is present at line in or mic? Is my above assumption correct that I *should* hear the signal when the two symbols, speaker and mic are not crossed out under the capture slider?

---

### Post by johann_p on 2008-07-28
I figured this out myself.

I downloaded the newest alsa-drivers package and compiled it myself. After installation, the alsamixer shows additional options: the relevant one is called "Analog loopback" and muted by default. Activating this makes the sound from the inputs (with the new version all 3 are shown too!) be passed through to the output!

---

### Post by markbuntu on 2008-07-28
I just checked mix in the gnome-alsa mixer.

---


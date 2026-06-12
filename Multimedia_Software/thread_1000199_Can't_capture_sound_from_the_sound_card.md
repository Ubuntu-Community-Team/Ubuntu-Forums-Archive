---
title: "Can't capture sound from the sound card"
date: 2008-12-02
forum: Multimedia Software
---

### Post by azangru on 2008-12-02
Hi! I'm on Ubuntu Hardy, and for whatever reason I can't capture sound from the sound card. Actually, I don't think I can record sound at all - the Sound Recorder just hangs when I press the record button.

It wasn't such a big deal, because I don't do much sound recording anyway, (I don't even have a microphone, so all the experiments were about capturing sound from the sound card) but today I wanted to record some video from my desktop, and installed gtk-RecordMyDesktop, but that program crashed complaining that it couldn't capture sound from the sound card (the error number 700-something; I can post it if it's important).

So. I am no expert in sound cards, but I know that mine works, because it can play sound files. Can you suggest any method to make Sound Recorder and gtk-RecordMyDesktop work nicely with my sound card.

---

### Post by andr3w on 2009-01-27
> **azangru said:**
> Hi! I'm on Ubuntu Hardy, and for whatever reason I can't capture sound from the sound card. Actually, I don't think I can record sound at all - the Sound Recorder just hangs when I press the record button.

It wasn't such a big deal, because I don't do much sound recording anyway, (I don't even have a microphone, so all the experiments were about capturing sound from the sound card) but today I wanted to record some video from my desktop, and installed gtk-RecordMyDesktop, but that program crashed complaining that it couldn't capture sound from the sound card (the error number 700-something; I can post it if it's important).

So. I am no expert in sound cards, but I know that mine works, because it can play sound files. Can you suggest any method to make Sound Recorder and gtk-RecordMyDesktop work nicely with my sound card.

I've gone to a lot of threads and no one answers this question.

---

### Post by markbuntu on 2009-01-27
To use sound recorder in Hardy or Intrepid you must first select the default Input Device in the pulseaudio volume control by right clicking on it. If you want to record whatever is playing through your speakers choose the monitor source for your soundcard.
You can use the pulseaudio vu meter (pavumeter) to monitor the levels.

---


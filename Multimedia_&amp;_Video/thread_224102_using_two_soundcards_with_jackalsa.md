---
title: "using two soundcards with jack/alsa"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by pjob on 2006-07-27
Hey,
I have two "sound cards":
- the Intel HDA integrated in my laptop
- and the card in my logitech usb headset (actually the socom headset)

I was wondering if there is a way to configure alsa or jack in such a way that i can use the mic on the headset as the input for the system and the intel card for the output tasks.

The goal is to record my acustic guitar and apply effects in real time (using something like jack-rack.. i dont quite know how im going to do this yet), then output the resulting audio to headphones, creating something like a pedal for my guitar.

I cant seem to find any nice way of doing this, so any help is appreciated.

is this possible?

---

### Post by bluecherry on 2006-07-27
Have you tried the qjackctl tool?

This GUI interface lets you create visual links between different (program and soundcard) in/outputs .

---

### Post by hippy4life on 2006-12-05
did you have any luck with this?

---

### Post by Aliby on 2008-01-14
I am trying to get this right too.
I have an onboard card and a SoundBlaster Live.

I cam across this page and it may provide us with the answers.
[http://quicktoots.linuxaudio.org/toots/el-cheapo/]("http://quicktoots.linuxaudio.org/toots/el-cheapo/")

I am not going to do the hardware sync (rather make use of Jask's latenecy compensation if there are differences). Certainly the ALSA config may help.

Let me know as will I....

:KS

---

### Post by Aliby on 2008-01-15
One resource I found was this:
[http://alsa.opensrc.org/index.php/TwoCardsAsOne]("http://alsa.opensrc.org/index.php/TwoCardsAsOne")

I am not sure how to enable syncing (preventing drift) using a wordclock which is my preference as I am not going to try the hardware mods suggested by **Timo Sivula** on his page:
[http://quicktoots.linuxaudio.org/toots/el-cheapo/]("http://quicktoots.linuxaudio.org/toots/el-cheapo/")

Keep in touch with your thoughts, discoveries and progress ....
:)

---


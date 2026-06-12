---
title: "USB-MIDI-Keyboard and QSynth via aconnect: Stops working after a while."
date: 2017-09-16
forum: Multimedia Software
---

### Post by rakm on 2017-09-16
I have connected a keyboard via USB and run Qsynth for piano sound synthesis from a soundfont file. I use aconnect to connect the keyboard and QSynth.
So far so good, easy enough.
However, around in the middle of playing a piano piece the sound synthesis will suddenly stop! Happens after maybe halfway through a 4-page piece.
When that happens the only way to remedy it (until it happens again) is to disconnect the keyboard from the USB port and plug it in again and subsequently run aconnect again to reestablish the connection with QSynth. After doing so I can sometimes hear the last note that didn't make it through when the previous session stopped working, it'll now suddenly play, as if it was stuck somewhere all this time. Now I can play a bit more but sound synthesis will "freeze" again after a short while.

---

### Post by rakm on 2017-09-19
Doesn't seem like anyone has an idea how to start tackling this problem, maybe?

---

### Post by rakm on 2017-09-22
Well, I figured it out:
The problem occurred on 3 out of 4 notebooks I tried to connect!
It happened with pulse as well as alsa and with jack as well as with aconnect. Happened with both timidity or qsynth.
What finally fixed it for the 3 notebooks where it didn't work was to not connect the keyboard's USB but instead the keyboard's MIDI-OUT to a Roland MIDI-to-USB adapter.
Apparently the keyboard's USB connection was "at fault", in combination with those 3 notebooks.

---


---
title: "[Ubuntu 12.10] No longer digital and analog audio output simultaneously"
date: 2012-10-27
forum: Multimedia Software
---

### Post by linuxfleming on 2012-10-27
Using Ubuntu 12.04 I could listen to music through my receiver (digital/spdif output) and PC speakers (analog/3.5mm jack) simultaneously. I don't know what the exact option was (something with duplex output?)

However, after installing Ubuntu 12.10 that option appears to be gone. I now have to choose whether I want to use the analog channel or the digital. Is the option to use the various channels simultaneously gone in 12.10 or do I need to tweak some settings somewhere? By the way, the audio channels work fine on their own (just not simultaneously).

Thanks in advance for any help on this!

Dimitry

---

### Post by linuxfleming on 2012-10-28
Oh well, I'm just going to split the s/pdif signal and send one line directly to my receiver and convert the other line from digital to analog (for my PC speakers).

---

### Post by linuxfleming on 2012-11-07
For anyone that's ever running into this problem, just have a look at [http://askubuntu.com/questions/57319/analog-and-digital-audio-output-at-the-same-time]("http://askubuntu.com/questions/57319/analog-and-digital-audio-output-at-the-same-time")

In short, just install paprefs (sudo apt-get install paprefs) and adjust settings in the 'simultaneously output' tab. Head back to the "Output" tab from pulseaudio sound preferences menu and choose 'simultaneous output'

---


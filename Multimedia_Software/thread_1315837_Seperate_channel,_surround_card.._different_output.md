---
title: "Seperate channel, surround card.. different output on each channel"
date: 2009-11-05
forum: Multimedia Software
---

### Post by torgils on 2009-11-05
I'm trying to make a 'home sound system'. 
One server, one amplifier for each room and supplementary speakers.

Is it possible to separate channels of a surroundcard with alsa or something else?
What I want to do is to use each channel as a 'room'.

Let's say, pc-room: plays metallica, bathroom: plays something else, bedroom: uses a script as alarm clock..

Excuse my english, but I'm trying ;)

---

### Post by markbuntu on 2009-11-05
You can probably use the channel map and naming functions in pulseaudio to map each channel separately and give it a unique name. You can read about pulseaudio here. There are some examples of re-mapping channels in the FAQ.

[http://www.pulseaudio.org/](http://www.pulseaudio.org/)

---

### Post by torgils on 2009-11-06
ok..
I will try that thank you..

---


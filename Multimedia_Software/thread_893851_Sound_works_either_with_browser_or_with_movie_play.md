---
title: "Sound works either with browser or with movie player"
date: 2008-08-18
forum: Multimedia Software
---

### Post by michiel33 on 2008-08-18
I have a strange sound problem (Ubuntu 8). When I run a movie in Firefox (eg Youtube) it has perfect sound. But then when I play a movie in Movie Player or VLC it has no sound. When I restart, movie player works but after running that, i have no sound in Firefox!

Any help is appreciated! Michiel

---

### Post by tuxxy on 2008-08-18
What are you using for sound output in system > prefs > sound, is it ALSA

---

### Post by kostkon on 2008-08-19
> **michiel33 said:**
> I have a strange sound problem (Ubuntu 8). When I run a movie in Firefox (eg Youtube) it has perfect sound. But then when I play a movie in Movie Player or VLC it has no sound. When I restart, movie player works but after running that, i have no sound in Firefox!

Any help is appreciated! Michiel
You have to install the *libflashsupport* package in order to make *Flash* to work with *PulseAudio*.

---

### Post by eye208 on 2008-08-19
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

### Post by michiel33 on 2008-08-22
> **tuxxy said:**
> What are you using for sound output in system > prefs > sound, is it ALSA
Thanks for your help. Yes I use ALSA. Would I be better off with Pulse? I will try.

---

### Post by merlin051 on 2008-08-22
try this thread, solved my problems

[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

### Post by michiel33 on 2008-08-22
> **merlin051 said:**
> try this thread, solved my problems

[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
Thanks very much, this seems to solve my sound problem!

---


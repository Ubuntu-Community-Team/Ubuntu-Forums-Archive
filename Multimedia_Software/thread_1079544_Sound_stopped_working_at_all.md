---
title: "Sound stopped working at all"
date: 2009-02-24
forum: Multimedia Software
---

### Post by arepaking on 2009-02-24
Hello experts,
I've been using pulse audio for more than 2 month without any issues at all. Suddenly the sound stopped working in my Ubuntu Intrepid Installation. The Pulse sever seems to detect the application that supposed to be playing an audio (as you can see in my attachment).

Does anyone knows what could I possible be missing here?

Thanks in advance,
AK

---

### Post by markbuntu on 2009-02-24
Maybe the stream is playing on the wrong output device. You can right click on the playing stream to change the Output device

---

### Post by Oobowo on 2009-03-09
Had exactly the same problem, check your gnome alsa-mixer for a volume slider called IEC958, set slider for full volume. This took me two days to figure out..oi!

hope it works

---

### Post by boooney on 2009-03-11
Hi All-

First my flash sound stopped working and now all of my sound has stopped working.  I notice that there are no output devices listed at all in the pulseaudio applet.  what can I do to get my sound back?  my sound card is a via82xx.

I noticed in the alsamixer control in terminal (using 'alsamixer -Dhw'), there is no way to turn up the master.  it seems stuck at 0.  I did turn up IEC958 P and it had no effect.

Thanks.

PS I'm using intrepid

---


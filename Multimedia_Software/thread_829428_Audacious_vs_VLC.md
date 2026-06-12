---
title: "Audacious vs VLC"
date: 2008-06-14
forum: Multimedia Software
---

### Post by vhadiant on 2008-06-14
Hi,

When Audacious is running my VLC can't output any sound. The video runs fine but. Did I somehow screw up my sound setting?

I've set Audacious to use ALSA, this should be the driver to use right?

---

### Post by zero777zero on 2008-06-26
i have this issue too.

if i'm playing audacious and start vlc, vlc gets no sound, when i shut down audacious, vlc gets sound, then when i shut down vlc and try to play audacious again, nothing plays, not just no audio, but song won't even start and timer doesnt appear.

have to reboot to get audacious to work again.

hardy heron ubuntu

---

### Post by zero777zero on 2008-06-26
ughhh, looks like youtube has the same effect on audacious

---

### Post by mastermindg on 2008-06-26
This is related to the use of PulseAudio. Both VLC and Audacious support PortAudio natively.

You need to set VLC to use PulseAudio (Advanced, Audio, Output Modules) and Audacious Simply Select "Preferences -> Audio -> Audio System -> PulseAudio Output Plugin".

---

### Post by zero777zero on 2008-06-26
awesome

([vlc guide]("http://www.alterego7.com/2008/04/vlc-with-pulseaudio-on-ubuntu-804.html"))

---


---
title: "Only One Program Plays Sound at a Time"
date: 2008-05-24
forum: Multimedia Software
---

### Post by Nin10dude on 2008-05-24
Since upgrading to Ubuntu 8.04, only one program can play sound at a time. I'm sure this is something caused by pulse, though I'm not sure what to do in order to fix this. Can anyone help me out?

---

### Post by Steve413z on 2008-05-24
I found the easiest way to resolve this problem, is to go back to ALSA sound, PulseAudio isn't working that well for me.

System > Preferences > Sound > set all devices to ALSA


theres some workarounds for pulseaudio, but this was the easiest solution for me.

---

### Post by Steve413z on 2008-05-24
you might have to reboot after you do this too

---

### Post by cariboo on 2008-05-24
Try this:

[http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+setup]("http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+setup")

It solved my problems of only audio from one program at a time.

Jim

---


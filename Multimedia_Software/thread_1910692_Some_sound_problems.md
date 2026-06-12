---
title: "Some sound problems"
date: 2012-01-17
forum: Multimedia Software
---

### Post by sakishrist on 2012-01-17
Hello,

I am having some strange problems with my sound. 

The most important is that pulseaudio randomly crashes and restarts (at least that's what I think happens). It mostly happens when I'm in a skype call. I have also noticed that it has started happening more often after I installed a package called pulseaudio-equalizer or something along those lines.

This brings me to my second problem. I have tried to uninstall pulseaudio equalizer but after doing so and restarting my system, the sound is exactly like when I was using the equalizer. So I am wondering how I could reset the settings so that this feature is not enabled at all even after uninstalling the equalizer.

Finally, I have a problem with vlc's sound. When I play some file and I pause, fast forward or rewind, there is a great chance the sound will stop. I am not sure whether this is a problem with pusle audio/alsa or with vlc. Another thing I should mention is that I use the daily ppa (I wanted to have 10-bit support and the current stable does not include it).

Thanks in advance
Sakis

---

### Post by MoreOrLess on 2012-01-17
Try to get a pulseaudio log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)
It may help.

---

### Post by sakishrist on 2012-01-21
OK, I have attached the log file and here is what happened in the terminal:```
sakishrist@sakishrist-pc:~$ LANG=C pulseaudio -vvvv --log-time=1 > ~/pulseverbe2.log 2>&1
Killed
sakishrist@sakishrist-pc:~$
```I couldn't upload it earlier because I didn't have any skype calls to make. But today, I had to make some calls and these are the results. I hope you can help me.

Thanks in advance!!!

EDIT: By the way, from the log I see that skype was set to automatically adjust the volume, so I am wondering whether that could be the problem. I'll give it a try without this option.

---


---
title: "microphone muted by alsamixer capture mix"
date: 2012-07-11
forum: Multimedia Software
---

### Post by doru001 on 2012-07-11
I remember that two months ago I could record my microphone through alsamixer's Capture Mix channel. However, now this does mute my microphone in the gnome-volume-control Input tab. 

The only change I made, besides regular updates, was to create an executable /etc/pm/sleep.d/50alsa containing: 
```
case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                /sbin/alsa force-reload
                ;;
        *) exit $NA
                ;;
esac
```
to enable for sound after hibernation. 

When I unmute the microphone in gnome-volume-control, alsamixer's Capture changes from Mix to Mic. When I change alsamixer's Capture from Mic to Mix, the microphone is muted in gnome-volume-control. How could this happen? :confused:

Distribution: Ubuntu 10.04 lts Lucid Desktop upgraded from 8.04 and using lubuntu on top of it. Kernel: 2.6.32-41-generic.

---


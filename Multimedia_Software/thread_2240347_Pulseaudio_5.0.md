---
title: "Pulseaudio 5.0"
date: 2014-08-19
forum: Multimedia Software
---

### Post by uudruid74 on 2014-08-19
I have one small issue with pulseaudio.  I want to be able to control it using the volume keys on my wireless keyboard, but I don't want it to touch the sound devices.  I want to control the current sound app.  Some applications will accept the proper hot-keys, which makes this easy.  For apps that don't, I want the system to launch a script (so far, all this is working), but I want the script to find the last client (easy again), and change the client volume - the same volume you'd change with the pavucontrol playback tab.   Here's the problem.  The pacmd program to control pulseaudio from the command line has a set-sink-volume and set-source-volume, but no set-client-volume.  I was wondering if any PA 5 users could check and see if "pacmd help" will list a set-client-volume command.   If so, I'll upgrade.  Otherwise, I can wait.

Thanks!

---

### Post by cariboo on 2014-08-19
Moved to multimedia.

---


---
title: "Pulseaudio Daemon startup failed"
date: 2011-08-21
forum: Multimedia Software
---

### Post by davethewave83 on 2011-08-21
pulseaudio --kill
pulseaudio -D 
**Daemon startup failed**
....

pulseaudio --check 
(nothin pops up) 

pulseaudio -k ; pulseaudio -D
Failed to kill daemon: No such process

pulseaudio --check 
(nothing again) 

sudo /etc/init.d/pulseaudio restart
 * PulseAudio configured for per-user sessions

pulseaudio --check
(nothing still) 

is there any way at all to restart the pulseaudio daemon? :confused:

---


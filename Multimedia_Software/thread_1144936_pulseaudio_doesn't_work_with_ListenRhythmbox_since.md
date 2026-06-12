---
title: "pulseaudio doesn't work with Listen/Rhythmbox since Jaunty upgrade"
date: 2009-05-01
forum: Multimedia Software
---

### Post by dehu on 2009-05-01
any other sound works except listen music player and rhythmbox, flash and videos and songbirds works properly, but Listen and Rhythmbox only shows up for less than a second in the playback/pulseaudio tab when playing a song and then disappears.
I tried the tutorial, but it didn't help
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

anyone knows what the problem could be or maybe even has a solution?

---

### Post by dehu on 2009-05-02
my output for pulseaudio
```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

and for aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---


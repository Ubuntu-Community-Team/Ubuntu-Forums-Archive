---
title: "Sound stopped working on Xubuntu 12.04.2"
date: 2013-07-13
forum: Multimedia Software
---

### Post by thatguymark on 2013-07-13
First I have tried a live CD (Zorin 6 Lite) and sound works there so I am confident it is a software issue. Speaker also works on other hardware.

Pulseaudio shows the activity of the stream under the Output Devices tab, but no sound comes out.

I've gone through the troubleshooting steps here:

help.ubuntu.com/community/SoundTroubleshooting

pulseaudio --kill and --check returns nothing, and -D shows 

```
E: [pulseaudio] main.c: Daemon startup failed.



```

Thoughts?

EDIT: Just to throw it out there I read something about permissions being a possible issue. As usual thanks in advance!

---

### Post by thatguymark on 2013-07-13
FWIW I also tried Volti with no success.

---

### Post by ajgreeny on 2013-07-13
If you haven't already done so run alsamixer in terminal and check that the levels of outputs are not set too low or muted.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "Playback" to "Capture" to "All".
In capture page use spacebar to enable the different input devices (mic, line, CD, video).
Esc will save and exit.

---

### Post by Yellow Pasque on 2013-07-13
Did you run:
```
rm -r ~/.pulse*; pulseaudio -k
```

---

### Post by thatguymark on 2013-08-04
Thanks for the replies guys, unfortunately neither of this did it. I got:


```
user@user-a1350n:~$ rm -r ~/.pulse*; pulseaudio -k
E: [pulseaudio] main.c: Failed to kill daemon: No such process
user@user-a1350n:~$ pulseaudio
E: [pulseaudio] main.c: D-Bus name org.PulseAudio1 already taken.
user@user-a1350n:~$
```

---


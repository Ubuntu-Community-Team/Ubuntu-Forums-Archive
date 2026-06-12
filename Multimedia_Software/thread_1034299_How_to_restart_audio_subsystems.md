---
title: "How to restart audio subsystems?"
date: 2009-01-08
forum: Multimedia Software
---

### Post by OliW on 2009-01-08
I'm having some real issues with sound recently. I'm not sure what the base or cause of the problem is but I do know the only way I can currently fix it is to do a full restart. With your help, I'd like to be able to cut that down to a few commands.

The general scenario is I'll be listening to something in amarok and it'll suddenly start stuttering the same few milliseconds of audio over and over again.

I've tried restarting ALSA (via /etc/init.d/alsa-utils restart) but this causes a short stop to the sound (while it's down) and upon it's re-arrival, the sound starts back up.

I can't seem to kill pulseaudio (which is where I believe the problem really is). I've tried issuing killall pulseaudio and /etc/init.d/pulseaudio stop commands but when I look in top, pulseaudio is still there (there are 4 threads if that makes any difference).

The pulseaudio manager is unresponsive. It locks up when trying to authenticate.

```
oli@bert:~/Desktop$ sudo pulseaudio -k
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: Failed to kill daemon.
```

```
oli@bert:~/Desktop$ lsof | grep pcm
# no output
```

```
oli@bert:~/Desktop$ ps aux | grep pulseaudio
oli      10108  3.0  0.6  48748 13476 ?        Ssl  Jan06  89:51 pulseaudio -D
oli      10114  0.0  0.1   7560  2456 ?        S    Jan06   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
```

Versions:
pulseaudio: 0.9.10-2ubuntu9.2
libasound2: 1.0.17a-0ubuntu4

---


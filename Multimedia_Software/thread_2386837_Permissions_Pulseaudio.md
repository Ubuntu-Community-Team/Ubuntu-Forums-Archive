---
title: "Permissions Pulseaudio"
date: 2018-03-11
forum: Multimedia Software
---

### Post by angel mike on 2018-03-11
Permission is denied to my Home directory with Pulseaudio.
```
michael@michael-XPS-11-9P33:~$ sudo pulseaudio
[sudo] password for michael: 
W: [pulseaudio] main.c: This program is not intended to be run as root (unless --system is specified).
E: [pulseaudio] core-util.c: Home directory not accessible: Permission denied
michael@michael-XPS-11-9P33:~$ 

```

---

### Post by ajgreeny on 2018-03-11
Why have you tried to run it with sudo as root?

Tell us more about your system; in most of the *ubuntu OSs (not Lubuntu IIRC) it should start by default at the start of the session.

---

### Post by angel mike on 2018-03-12
Thanks aigreeny - Am using Ubuntu 16.04 and have lost the sound. Could not get Pulseaudio to work or amixer. Permission to Home directory denied. Purged/reinstalled  Alsa and Pulseaudio. Mike

---


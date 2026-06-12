---
title: "Starting PulseAudio without Gnome (IceWM + XDM)"
date: 2009-06-15
forum: Multimedia Software
---

### Post by whocarez on 2009-06-15
I am using Ubuntu 9.04, and have removed all Gnome packages. My primary desktop i IceWM with XDM. I noticed that Gnome has a startup-script for PulseAudio in /etc/X11/Xsession.d/70pulseaudio, which I guess is the primary method for starting pulseaudio. I also noticed that there is a script, /usr/bin/start-pulseaudio-x11 which essentially starts PulseAudio and loads some pa-modules.

My question is how to start PulseAudio correctly on login. Should I just create a small script in /etc/X11/Xsession.d that executes pulseaudio through the start-pulseaudio-x11 script?

Looks like I also had to add myself to pulse-rt and pulse-access groups. I think it would be nice if Ubuntu also provided scripts for starting PulseAudio without having Gnome installed. Maybe in a small package, so it is not Gnome dependent.

---

### Post by whocarez on 2009-06-17
A small bump, I guess..

---

### Post by Forlornity on 2009-06-18
If it helps, I tend to start pulseaudio (after the frequent crashes) with the command:
```
pulseaudio --start
```

---

### Post by markbuntu on 2009-06-18
pulseaudio -D will start pulse as a daemon.

---


---
title: "[help] alsamixer settings not saved on reboot"
date: 2009-10-26
forum: Multimedia Software
---

### Post by weaktight on 2009-10-26
I'm running ubuntu on an Ion Asrock.

S/PDIF 1 is muted when I boot.  Master and Line levels are also 0, but that doesn't matter.

I have to SSH in to unmute it via alsamixer everytime I start the box.  I'm using hdmi audio.

I've tried the following to no avail (with and without sudo):
```
alsactl store 0
```

I'm running ubuntu 9.04 and alsa version 1.0.21

If anyone has a suggestion, it would be appreciated.

---

### Post by AutoStatic on 2009-10-26
Hello weaktight, you could try the following:
- Set up your mixer settings
- Save them with the command **alsactl store -f $HOME/Desktop/asound.state** This will save the settings on your desktop in a file called *asound.state*
- Make a copy of /etc/asound.state if it exists with **sudo cp /etc/asound.state /etc/asound.state.orig**
- Copy your saved settings from your Desktop to the /etc directory with **sudo cp /home/yourusername/Desktop/asound.state /etc/asound.state**

---

### Post by weaktight on 2009-10-26
This didn't work.

In fact, /etc/asound.state is the same before and after I unmute and run 'sudo alsactl store'.  If I run 'aslctl store -f file' to a file after the unmute, it's identical to /etc/asound.state as well.  I verified this with diff.

Where is the mute/unmute information stored?

---


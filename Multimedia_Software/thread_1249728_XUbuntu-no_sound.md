---
title: "XUbuntu-no sound"
date: 2009-08-25
forum: Multimedia Software
---

### Post by linuxhippy on 2009-08-25
I just installed XUbuntu 9.04 on a 64 bit desktop and have no sound.  My soundcard was detected and I'm able to turn up the volume in alsamixer and the xfce mixer.  Here's a screenshot of alsamixer and my ESS Solo PCI sound card:

[IMG]http://linuxhippy.servemp3.com:8001/alsamixer.jpg[/IMG]

What am I missing here?

---

### Post by jjalocha on 2009-08-25
According to the screenshot, your Master is Muted (see the MM?) You should press the M key to unmute it (change MM to OO).

---

### Post by linuxhippy on 2009-08-25
> **jjalocha said:**
> According to the screenshot, your Master is Muted (see the MM?) You should press the M key to unmute it (change MM to OO).

wow-that was it!  The sounds are garbly...maybe a reboot is needed but at least I have sound now.

---

### Post by bagy on 2009-09-05
Try sudo alsa force-reload i fix the sound problem...:))

---

### Post by Jose Catre-Vandis on 2009-09-05
To save the settings:
```
sudo alsactl store
```

---


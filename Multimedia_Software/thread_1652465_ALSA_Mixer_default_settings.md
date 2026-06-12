---
title: "ALSA Mixer default settings"
date: 2010-12-24
forum: Multimedia Software
---

### Post by demibatard on 2010-12-24
Hello,

I notice that each time I boot my computer, under the playback section of the ALSA Mixer the 'Speaker' volume control is turned all the way down. Even when I return it to the proper level, and then restart my computer later, the slider for 'Speaker' seems to default back to the previous state mentioned above.

Is there a way to set the default for the ALSA mixer in a .conf file of some sort so that the default setting for 'Speaker' is always at max?

Thanks,
demibatard :)

---

### Post by demibatard on 2010-12-24
Also, I tried using the command:

```
sudo alsactl store
```

But that did not correct the problem. Any ideas?

---

### Post by lidex on 2010-12-25
The command to save alsamixer settings is:
```
sudo alsactl store 0
```
Does your install use pulseaudio?

---

### Post by demibatard on 2010-12-25
Yes, I tried the command you suggested but it did not work. I also do have PulseAudio installed, although I don't believe I ever have used it.

---

### Post by lidex on 2010-12-26
OK. Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

---


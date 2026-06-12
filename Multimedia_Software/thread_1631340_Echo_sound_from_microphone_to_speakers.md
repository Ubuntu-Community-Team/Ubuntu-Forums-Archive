---
title: "Echo sound from microphone to speakers"
date: 2010-11-26
forum: Multimedia Software
---

### Post by imgx64 on 2010-11-26
How can I echo the sound from the microphone to the speakers?

I.e., anything that is picked up by the microphone is played on the speakers immediately, without recording anything. Preferably with the ability to increase the volume.

---

### Post by gordintoronto on 2010-11-26
That is the default behaviour if nothing is muted.

---

### Post by imgx64 on 2010-11-26
> **gordintoronto said:**
> That is the default behaviour if nothing is muted.

Doesn't seem to be the case for me. I checked all tabs in Sound Preferences and nothing is muted. What else might be muted?

Before you ask, I'm sure the microphone is working because I can use Sound Recorder to record and play sound.

---

### Post by imgx64 on 2010-11-27
I found the solution here: [http://ubuntuforums.org/showthread.php?t=1324135](http://ubuntuforums.org/showthread.php?t=1324135)

For the curious:
```
$ pactl load-module module-loopback
```
turns it on, and:

```
$ sudo sh -c 'echo "load-module module-loopback" >> /etc/pulse/default.pa'
```
makes it permanent.

---


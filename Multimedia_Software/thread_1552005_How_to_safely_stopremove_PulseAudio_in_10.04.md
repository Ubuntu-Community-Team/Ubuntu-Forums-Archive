---
title: "How to safely stop/remove PulseAudio in 10.04"
date: 2010-08-13
forum: Multimedia Software
---

### Post by Emanuele_Z on 2010-08-13
Hi all,

Is there a guide on how to (safely) stop/start the PulseAudio infrastructure in 10.04?
Apparently PulseAudio might be causing slowness and I'd like to test an application with the whole PulseAudio Infrastructure disabled (not just pasuspender).

Thanks,

---

### Post by FeraTech on 2010-08-23
I have no idea why they are bothering with PulseAudio. Nearly every single problem with the audio can be fixed by removing this garbage. The advantages of even having pulse can not justify having it installed by default by any stretch of the imagination.

> sudo apt-get autoremove pulseaudio

---

### Post by whit on 2010-08-23
I'd love to deep-six pulse. Really. But just removing it doesn't make sound work. Please give an entire recipe for success, if you're going to urge that.

---

### Post by AutoStatic on 2010-08-24
Despite the FUD:
[LIST]
[*]Create a new file */home/yourusername/.pulse/client.con*f with one single line:```
autospawn = no
```
[*]Kill PulseAudio with the command **pulseaudio -k**
[/LIST]

And enjoy a desktop session with a lot of applications that can't output sound at the same time or just remain mute.

---

### Post by toddr on 2010-08-30
This worked for me on a fresh install of 10.04:

[http://ubuntuforums.org/showthread.php?t=1313253](http://ubuntuforums.org/showthread.php?t=1313253)

---

### Post by go_beep_yourself on 2011-07-18
+1 thx :popcorn:

---


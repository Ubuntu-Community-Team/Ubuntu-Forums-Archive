---
title: "Microphone problems in ALSA, Dapper"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by mb108 on 2006-11-03
I had some issues with getting sounds from more than one application, and somebody pointed me to [this howto]("http://ubuntuforums.org/showthread.php?t=44753"). Worked great.

Now I've got a mic to add into the equation.

I checked my alsamixer settings, I have mic and capture enabled (in the capture tab), w/ capture turned all the way up. It appears I cannot turn up the volume on mic. I have attached the amixer output and asound.conf.

I CAN hear myself through the speakers. This is progress, right?

However:
* Gnome sound recorder, upon pressing "Record", pops up with "Could not get/set settings from/on resource."
* Tried Multimedia Sound Selector (enabled in Preferences menu with Alacarte), when I press test i get the same message
* I tried "arecord test.wav" and got this:

```
Recording WAVE 'test.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono arecord: set_params:896: Sample format non available
```
* Running Ventrilo with Wine (the end goal), no mic is recognized. I can give specific error messages if requested, but it is along the same lines: cannot access device.

.... but like I said, I can hear myself fine through the speakers.

Any help appreciated.

---

### Post by mb108 on 2006-11-07
Anybody have any ideas?

---

### Post by mb108 on 2006-11-10
Fixed. 

Go to system > preferences > multimedia systems selector
Change input to OSS

---


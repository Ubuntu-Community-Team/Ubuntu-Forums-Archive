---
title: "Do I serously need windows to record sound output?"
date: 2010-03-20
forum: Multimedia Software
---

### Post by d3v1150m471c on 2010-03-20
This is absolutely ridiculous. I will start off by saying my mic and sound both work fine. I want to capture sound from my output. It seems like it would be an easy task.

Things that have failed:

Audacity - (hw:0,0) and (hw:0,2) both fail to record sound except from the mic input. Default is of course already my mic. Audacity is supposed to have a mix option for recording which is missing.

arecord :
```

d3v11@d3v11m4ch1n3:~$ arecord -d 10 -c 2 -r 44100 -t wav -D copy foobar.wav
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM copy
arecord: main:608: audio open error: No such file or directory

```

pa-clone also failed. A, I use alsa and not pulseaudio, B. installing the things it needs to run will most likely break my sound.

I am beginning to think it's just impossible to accomplish this. Do I seriously have to resort to windows just to record my sound output?

---

### Post by d3v1150m471c on 2010-03-23
bump

```

d3v11@d3v11m4ch1n3:~$ ls /proc/asound
card0  devices  Intel    oss  seq     version
cards  hwdep    modules  pcm  timers         
d3v11@d3v11m4ch1n3:~$ ls /proc/asound/Intel
codec#0  codec#1  id  oss_mixer  pcm0c  pcm0p  pcm2c
d3v11@d3v11m4ch1n3:~$ cat /proc/asound/Intel/pcm0p/info
card: 0                                                
device: 0
subdevice: 0
stream: PLAYBACK
id: ALC268 Analog
name: ALC268 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1
d3v11@d3v11m4ch1n3:~$ cat /proc/asound/Intel/pcm0c/info
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC268 Analog
name: ALC268 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1
d3v11@d3v11m4ch1n3:~$

```

---

### Post by mbuller10 on 2010-05-03
bump

---

### Post by pmooney78 on 2010-05-26
Try this: [http://ubuntuforums.org/showthread.php?t=1330728](http://ubuntuforums.org/showthread.php?t=1330728)

---


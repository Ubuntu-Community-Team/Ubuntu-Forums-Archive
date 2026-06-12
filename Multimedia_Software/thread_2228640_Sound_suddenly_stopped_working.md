---
title: "Sound suddenly stopped working"
date: 2014-06-08
forum: Multimedia Software
---

### Post by nikolai2 on 2014-06-08
I am running Ubuntu 14.04LTS and all of a sudden the sound stopped working. The drivers are displayed in the sound settings but when i attempt to click test sound nothing pops up :confused:. I've tried switching from the open source drivers to the propriety drivers but still no sound. Has anyone on 14.04 had this problem and does anyone know how to fix it?

---

### Post by fr-andres on 2014-06-08
Hi, I had this problem on U12, the pulseaudio server seems to be problematic... Let's see if I can help you (I'm not an expert):
One possible reason could be if your ALSA mixer has any muted channel. Try to open a terminal and take a look to "alsamixer", you may have any volume bar at zero...
You may also take a look/post here the result of "amixer".
I hope it helps!
Andres
EDIT: oh, sorry, I misunderstood the question. If the test window doesn't pop up it is probably not a problem with the alsa mixer :roll:
So probably the problem is that your soundcard is recognized by ubuntu but not by pulseaudio, did you try to restart it with "pulseaudio -k"?
Or you can try to install "pavucontrol" and "pavumeter" and fiddle with them... sorry if I can't help further i'm not that good!
cheers

---

### Post by Yellow Pasque on 2014-06-09
Which device are you trying to use?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by ryank76nz on 2014-06-09
I'm having this problem too. 14.04 xubuntu. My info is here:
[http://www.alsa-project.org/db/?f=48bc70e7f3ef8af3664b29f49b29b06c7ea48aef](http://www.alsa-project.org/db/?f=48bc70e7f3ef8af3664b29f49b29b06c7ea48aef)

all worked fine when I installed about a month ago.

---

### Post by ryank76nz on 2014-06-10
I'm using xbuntu, should I post a new thread? It's the same problem. An update about 3 weeks ago broke sound in the same manner described.

---

### Post by Yellow Pasque on 2014-06-12
@ryan: which sound device are you trying to use (onboard audio or HDMI audio)?

---

### Post by ryank76nz on 2014-06-15
Hi, thanks for reply. The Volume Control Settings only give me the option of:

HDMI/Display Port (plugged in) 


on the Output Devices tab.

Happy to use whatever works, but I don't completely understand the options.

---

### Post by ryank76nz on 2014-06-16
Ok it's started randomly working again. No idea on that. Maybe an update fixed it.

---

### Post by ryank76nz on 2014-06-16
Ok it's started randomly working again. No idea on that. Maybe an update fixed it.

---


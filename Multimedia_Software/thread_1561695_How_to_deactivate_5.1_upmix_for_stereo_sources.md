---
title: "How to deactivate 5.1 upmix for stereo sources"
date: 2010-08-26
forum: Multimedia Software
---

### Post by /dev/zero on 2010-08-26
Hello,

I've got a stock amd64 ubuntu 10.04 install and everything works great. I've got a 5.1 soundcard and speaker system and while it's great for DVD and other 5.1 audio sources, I don't like my stereo sources to be upmixed to 5.1.
I've searched this forum for "upmix" and all I have found is old threads to activate upmixing  from 2.0 to 5.1. With 10.04 it's already upmixed and I didn't found how to keep 2.0 sound to the front speakers (while keeping 5.1 sound to my 5+1 speakers).

I welcome any input.

Ps: forget my French, I'm English (or maybe the other way around)

---

### Post by /dev/zero on 2010-08-27
bump

---

### Post by Yellow Pasque on 2010-08-27
You might try disabling upmixing in /etc/pulse/daemon.conf so that only native 5.1 apps produce surround sound.

```
gksu gedit /etc/pulse/daemon.conf
```
Find line that says:
```
; enable-remixing = yes
```
Change to -->
```
enable-remixing = no
```
Save. Quit. Kill pulseaudio to restart it (or log out and log in)
```
pulseaudio --kill
```

---

### Post by /dev/zero on 2010-09-02
Thank's it's exactly what I want.

---


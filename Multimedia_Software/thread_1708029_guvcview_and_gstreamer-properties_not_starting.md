---
title: "guvcview and gstreamer-properties not starting"
date: 2011-03-16
forum: Multimedia Software
---

### Post by lonemangx on 2011-03-16
I don't know what caused this but running guvcview does not show any gui anymore. Using terminal I have the ff message:
```
guvcview 1.4.1
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0
```I can't also access gstreamer-properties, it shows a blank window however, and I can't close it without ending it using system monitor. Using terminal I have the ff message:
```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
```It's fine the last time I used this which is about two weeks ago, I don't know if the recent updates did this. I reinstalled it but nothing happened. Hope someone could help.

---

### Post by no2498 on 2011-03-16
try sudo gstreamer-properties

---

### Post by someitalian123 on 2011-06-10
With me no window pops up, and I get this in the terminal

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'

I tried sudo gstreamer-properties, it did nothing

---

### Post by no2498 on 2011-06-11
open your package manager and see if you have 
gstreamer good , bad , ugly , and .010 for the linux/ubuntu you use

everyone get some of these

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
 gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
 gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
 gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
 gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
 gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
 gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
 gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'

---


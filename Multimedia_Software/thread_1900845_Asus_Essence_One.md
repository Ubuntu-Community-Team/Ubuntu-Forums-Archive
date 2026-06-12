---
title: "Asus Essence One"
date: 2011-12-27
forum: Multimedia Software
---

### Post by stfb on 2011-12-27
I thought of opening this thread to share our experience on this device as I found nothing available on forums up to now.
First, good news : it's working perfectly on Ubuntu (I have Kubuntu 11.10. I had to disable the motherboard embeded audio first).

2nd: There is a way to make the perfect bit working on linux. I succeeded to make it work with VLC. You need to go to the settings and choose "Alsa audio output" as the output module (audio section) and choose "ASUS Xonar..." as the device.
Then when you play audio files, the essence will switch automatically to the actual sampling rate (but the perfect bit led will not light up ...).
No more oversmapling from pulseaudio :-)

---

### Post by feax on 2012-05-12
When using pulseaudio with amarok, it seems the sound is better if you make:


sudo gedit /etc/pulse/daemon.conf

then replace      
resample-method = speex-float-1  

 by  

; resample-method = speex-float-1

replace :
;default-sample-format = s24be
;default-sample-rate = 44100

by

default-sample-format = s24be
default-sample-rate = 44100

---

### Post by feax on 2012-09-03
For the best sound, you have to use these settings:

; resample-method = speex-float-1
instead of 
resample-method = speex-float-1  


default-sample-format = float32be
default-sample-rate = 192000

instead of

default-sample-format = s16le
default-sample-rate = 44100

[http://doc.ubuntu-fr.org/pulseaudio](http://doc.ubuntu-fr.org/pulseaudio)



The ideal would be to have  hifi sound when switching to essence one output , and returning to normal sound when switching usual sound output

---


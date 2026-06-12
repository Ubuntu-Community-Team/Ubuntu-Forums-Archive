---
title: "Microphone in flash 10"
date: 2010-02-15
forum: Multimedia Software
---

### Post by daboo911 on 2010-02-15
I've been trying to get my webcam microphone working in flash on Kubuntu 9.10.  I have a Logitek Pro 9000, and video and audio work in other applications (skype), but video is all that works in flash (I have flash 10 installed).  In the flash settings, it lists the only microphone option as "Linux Microphone", which does nothing.  This seems to be a common problem, with a few solutions offered.

One I've tried, which seems fairly straightforward for gnome users, is [here]("http://www.nikolakis.net/2010/01/make-webcam-mic-work-with-flash-in-ubuntu/").  However, whenever I run pavucontrol, I get an error reading "Connection failed: Connection refused".

Does anyone know how to either get pulseaudio open, or how to get the microphone working in flash without it?

Thanks so much

---

### Post by Bedpan.ca on 2010-03-26
Any luck fixing it yet?

---

### Post by async128 on 2010-07-21
had the same problem with SKYPE beta 2.1 with 10.04 and only got Pulseaudio server local as the mic. but Video aok. There was with no option to change from pulseaudio. On SKYPE test call there was no sound recording. 

I fixed simply by changing MIC device as follows:-

System/preferences/sound/input then  change device to logitek 9000 mono audio. Then reboot and do SKYPE audio test..

Whopps acidently posted reply in wrong thread

---


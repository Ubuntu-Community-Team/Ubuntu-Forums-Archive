---
title: "Crackling input sound in Toshiba Satellite A210-139"
date: 2011-06-16
forum: Multimedia Software
---

### Post by maelstr0m on 2011-06-16
I recently installed Ubuntu Natty on my Toshiba Satellite A210-139. Everything works fine except the microphone. I can hear a crackling sound also when I record using Sound Recorder, but it's not too bad.
The big issue is with skype, where, besides an annoying, loud white noise, the receiver hears me quite intermittently.

I tried many things. Firstly, I played around with Alsamixer and Pulseaudio with every possible combination. Didn't work.

I also tried what seemed to solve the problem to many users: replacing
```
load-module module-udev-detect
```with
```
load-module module-udev-detect tsched=0
```in /etc/pulse/default.pa

Also this didn't solve the problem.

Any help?

---

### Post by lidex on 2011-06-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---


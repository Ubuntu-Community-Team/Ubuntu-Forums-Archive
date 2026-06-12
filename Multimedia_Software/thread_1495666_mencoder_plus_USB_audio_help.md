---
title: "mencoder plus USB audio help"
date: 2010-05-28
forum: Multimedia Software
---

### Post by [censored] on 2010-05-28
Hi I'm trying to access my web cam, and use my Edirol UA25 USB audio interface to capture the audio. When the interface is plugged in, its recognized as device "hw:1" according to Jack Control. Unfortunately I can't work out how to get mencoder to recognize that device.

I've been using the mencoder instructions here: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

I've tried using the command ......

> mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o test.avi

...... substituting /dev/dsp with "hw:1", "hw1", "hw.1" and various other things, but I just errors like "Unable to open 'hw1': No such file or directory".

So does anyone know how to get mencoder to use hw:1 ?

---


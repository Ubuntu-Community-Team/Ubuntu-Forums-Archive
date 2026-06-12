---
title: "ubuntu studio record jack audio output"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by librano on 2007-01-23
hi all

I am using Ubuntu Studio built on Ubuntu Dapper Drake following the guide on the Ubuntu Studio site... (the old guide as they plan to make it a separate distribution a la Ubuntu Christian Edition).

I have got Jack audio server to work with a Creox (a program for adding effects to audio input from a guitar). I get sound out of my speakers but I cant seem to be able to record the output. Ubuntu Sound Recorder doesnt work with Jack and I cant configure that using the the GUI tools. Audacity doesnt detect any sound server Jack, ALSA or otherwise, Ardour is quite plainly a maze of a program, QARecord doesnt have any kind of preference settings in the GUI and doesnt detect the output from jack, etc etc. The closest I have got is JACK TimeMachine which seems to be the only recording program detected by Jack (I am using JACK Audio Connection Kit). However, the output file is in .w64 format. And I cant play this file even using VLC player.

What am I doing wrong? Any pointers, help, anything... I have been at this on and of ever since Dapper Drake came out... If you need more info just say the word... and how to obtain the info... ie which file to check or what to run on terminal.

lib

---

### Post by sebmdt on 2007-05-18
to convert files which are in w64 format (output of timemachine), you could use the command:

```
sndfile-convert  -pcm16    file.w64  file.wav
```

sndfile-convert is part of the sndfile-programs package

---


---
title: "Jack Audio kills speaker output"
date: 2020-06-20
forum: Multimedia Software
---

### Post by dgarlock2 on 2020-06-20
Greetings:
I have tried off and on for several weeks to use the Jack Audio Connection kit with my system.  I am running Ubuntu 18.04 and have both qjackctl and Cadence.  I can start the Jack server and the Source and Sink appear in my audio settings.  I can connect it to Mixxx and other apps.  The problem is that when Jack is running, I can get no sound through the speakers.  I have tried setting the output to Speakers, Jack Sink and both analog and digital audio, to no avail. In Jack set up the parameters are set to hw:Generic,0 for Interface and Output. The startup script is pactl load-module module-jack-sink and the after startup script is pacmd set-default-sink jack_out. Any ideas?  Also, I have been assuming that inputs connected to Jack Source automatically come out at Jack Sink.  If not, do they have to be connected?

---

### Post by dgarlock2 on 2020-07-24
Since it appears that no one on this forum has any experience with Jack, does anyone know of a good place to ask the question?  Thanks!

---


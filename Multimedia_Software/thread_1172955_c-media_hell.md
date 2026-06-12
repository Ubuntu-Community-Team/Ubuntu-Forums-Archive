---
title: "c-media hell"
date: 2009-05-29
forum: Multimedia Software
---

### Post by MimziM on 2009-05-29
hey im new to linux
but a reasonably fast learner
im running ubuntu with kubuntu besktop installed
,still using gnome gui
can anyone tell me how to get 5.1 sound with
the c-media cm8738 sound card
first it would only recognize 2 jacks
managed to get more sound by changing mode of line in or mic in
but no matter what,  no sound from subwoofer
please help , dont want to have install another instance of xp(yuk)

---

### Post by madverb on 2009-05-29
Do a search for Pulseaudio Howto. Sorted out a lot of problems for me.

---

### Post by MimziM on 2009-05-29
thanks, got all speakers working, but cannot adjust sound 
on individual speakers, but hey i was prepared to have no sound
to stay away from windows :-)
if anyone ekse has the same problem
pulse set to 2 channel default

[B]sudo gedit /etc/pulse/daemon.conf

[/B]scroll down to lines:
[B]
; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2

[/B]From ;[B]; default-sample-channels = 2 
[/B]remove "**;**" and set channels value to number of
speakers .eg. 2.1=3 , 5.1=6 , 7.1=8
will work most configurations

---


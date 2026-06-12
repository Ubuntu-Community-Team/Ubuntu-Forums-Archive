---
title: "Ubuntu Natty Narwhal freezes when playing music or video"
date: 2011-05-21
forum: Multimedia Software
---

### Post by Canaryguy on 2011-05-21
Greetings,

I'm using Ubuntu 11.04 x32 with Unity interface in Samsung N150 Plus.

It has been happening for a while that when I try to play music (I think it doesn't have anything to do with the music player but I'm using VLC) sometimes after the player has been playing the music Ubuntu freezes. I cannot move the mouse, the hard disk starts doing something during all this time. Sometimes the hard disk finishes whatever it is doing and then I can control the system again, and sometimes I just have to force a shutdown with the power button.

I have read posts about people saying that the system freezes but before they can play the files. Here the music or the video plays for sometime until all of a sudden everything is blocked and the hard disk is working crazy.

Is anybody having the same problem?

---

### Post by Phoenix87 on 2011-06-23
Please have a look at this bug report

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/799347]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/799347")

It seems to me that you are experiencing the same bug as me. I managed to temporary solve this issue by disabling pulseaudio. I hope this would get solved asap, for u must use alsamixer from a terminal to regulate the volume (otherwise u have to mess around with packages and so).

---

### Post by jwalters on 2011-07-02
I'm having the same problem . . . DVD plays for a while perfectly, then freezes. . . any fix yet?

---

### Post by Canaryguy on 2011-07-02
I recently replaced Unity for Gnome 3 to try it out and so far I like it. The videos that I've played with VLC have worked without problems although I haven't played many videos. Could Unity be causing the freezing problem? I'll see if the problem appears again in Gnome 3

---


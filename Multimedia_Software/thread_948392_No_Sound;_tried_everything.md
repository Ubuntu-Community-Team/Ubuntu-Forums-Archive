---
title: "No Sound; tried everything"
date: 2008-10-15
forum: Multimedia Software
---

### Post by melvnatic on 2008-10-15
I have a Dell mini 9. I recently installed Ubuntu, but after doing so, I could no longer use sound. I tried virtually everything I could find on the net, but nothing worked...

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) => I went here, tried everything, and nothing worked (although all the tests gave 'success')

[https://answers.launchpad.net/ubuntu/+question/5455](https://answers.launchpad.net/ubuntu/+question/5455) => tried suggestions of people here, nothing.

Tried updating alsa...rebuilding alsa...adding lines to alsa-base file...removing lines from alsa-bas file...random commands like modprobe...resetting alsa...you name it, I've done it. 

Anyone have any idea what I can do?

---

### Post by BMWDriver on 2008-10-15
My problem was being on the S/PDIF connector of my sound card. By default it's turned off. For that, I used the command [COLOR="Blue"]alsamixer[/COLOR]. This starts the mixer in your terminal. Use "m" to mute and unmute parts of the audio, and the left and right arrows to navigate, up and down arrows to lower or higher the volume output. Green means the channel is unmuted. You can also issue the command [COLOR="#0000ff"]man alsamixer[/COLOR] to read through the manual.

---

### Post by melvnatic on 2008-10-15
Yes; I have also already tried that :P But thanks for the reply. Anyone else?

Maybe I should mention that even the system beep and stuff when I enter bio setup is turned off.

Does anyone know if 82801G ICH7 even works with ubuntu??

---

### Post by BMWDriver on 2008-10-16
Yeah, I figured you might have after checking out your links. I've been lazy.

What about headphones ? This could well be physically related. If it's still under warranty, I'd check with Dell. Seems they sell them (in Canada anyway) with Ubuntu installed, so it should work with Ubuntu regardless.

Since the tests all gave success, there are no problems with the embedded sound chip !

---


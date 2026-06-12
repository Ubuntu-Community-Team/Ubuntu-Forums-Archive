---
title: "Playing simultanious audio streams fails!"
date: 2008-06-17
forum: Multimedia Software
---

### Post by hemajith on 2008-06-17
I'm using skype t call my friends on Hardy Heron. When I use Skype on Windows I can play mp3 while talking to a friend and he/she can hear it over there too. But when I try the same thing in Skype in Hardy, only one stream will work, either the call or the mp3 but not together! I tried playing the mp3 and while it's going on, to call my friend, but it says audio is already in use! Is there anyway I can get this to work?

---

### Post by bufsabre666 on 2008-06-17
system->preferences-> sound

change music and movies to autodetect

this will allow two differnt audio sources

---

### Post by markbuntu on 2008-06-17
If that doesn't work for you get this with synaptic:

libesd-alsa0

It is the Enlightened Sound Demon and allows multiple audio steams on one device.

---

### Post by hemajith on 2008-06-17
I do have the settings above and got libesd-alsa0 installed. Just to be sure I reinstalled it and restarted the system too. But the problem is still there. When a mp3 is playing, if I try to make a call on skype, it says "problem with audio playback" or if I try playing a mp3 while I'm on a call, the audio application gets stuck!

---


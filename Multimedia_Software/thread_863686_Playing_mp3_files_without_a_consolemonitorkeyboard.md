---
title: "Playing mp3 files without a console/monitor/keyboard"
date: 2008-07-18
forum: Multimedia Software
---

### Post by PlexorAB on 2008-07-18
I have a server in the kitchen running Ubuntu Server 8.04 where all my mp3-files are stored. It has a soundcard and speakers connected to it. The only probles is that the server has no keyboard, mouse or screen. Is there any kind of software i can use to be able to play mp3-files that have a kind of remote control (like a HTML-gui or similar) ?

I am using SSH today to login to the server and play music with mpg123, but that's a complicated way of doing it.

---

### Post by Jose Catre-Vandis on 2008-07-26
Have you got a desktop / X setup/running on the server (or could run). you could ssh -X and run a gui mp3 player on your remote desktop, or if you run a full desktop on the server you could vnc in and then run something like audacious from there. If you use resumable sessions you can leave the vnc session and the session continues. I'll need to go and find the command that lets you start running something with ssh and then leave the session. I am about to setup a similar thing with my server in the garage (for when I am working out there)

MPD might also be a suitable choice for this?

---


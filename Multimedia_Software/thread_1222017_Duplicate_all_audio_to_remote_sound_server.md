---
title: "Duplicate all audio to remote sound server"
date: 2009-07-24
forum: Multimedia Software
---

### Post by jnorth on 2009-07-24
I am trying to figure out a way to remotely duplicate sound.  I.e. I have a audio workstation in my control room, and I have a couple of servers in other offices around the building.  I would like to be able to connect speakers to those other servers and hear everything going on on the workstation side for monitoring/etc.  Would like it to be as close to real time as possible but I understand and can accept a few milliseconds of network delay.
Catch is, I would like it to send everything - not just reroute one program.  I know I can use mpd and a client software to play audio files, but I am looking more for something that would interface with pulseaudio and forward it all.

---

### Post by markbuntu on 2009-07-24
pulseaudio can do that all by itself. You just need to set up Multicast/RTP in Pulse Audio Preferences. there is an old how-to here that should still work


[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio)

You can also look here

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

---


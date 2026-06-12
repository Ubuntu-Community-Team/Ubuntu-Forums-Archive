---
title: "mpd is silent"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by eklitzke on 2006-11-05
Hi everyone,

I have mpd installed on a computer running Edgy Eft with the server install. I am trying to play audio from another computer running an mpd client.

All of the clients that I have tried can connect to the mpd server fine, and appear to play audio, but nothing comes out of the speakers. The volume is turned up to 100% on the clients. When I install mpd locally on the computer with the mpd client and connect to the local mpd server, things work correctly.

How can I troubleshoot this issue? I don't have speakers to use with the server, but alsamixer picks up my sound card and the sound is turned up on all the relevant channels.

Thanks,
Evan

---

### Post by quux on 2006-11-05
Hi, mpd does not stream the music to the client, but rather plays  the music on the server. So for using mpd you would have to connect your speakers to the server.

Maybe you should go for a streaming server that streams the music to a client ("apt-cache search mp3 streaming") and use a regular mp3 player app there.

---


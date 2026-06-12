---
title: "MPD Alternatives"
date: 2011-07-04
forum: Multimedia Software
---

### Post by motermouth15 on 2011-07-04
My MPD always crashes while i'm listening to music, but only when its changing songs, or i'm editing the playlists. I'm currently running it on a headless ubuntu server so that i can have my speaker system hooked up to it and control it from any other wifi enabled device. I'm wondering if there is another music server that will output the music on its own hardware and not stream. Any ideas?

---

### Post by nothingspecial on 2011-07-05
There is logitechs squeezeboxserver

[http://www.mysqueezebox.com/download](http://www.mysqueezebox.com/download)

They have great hardware for it but you don't need it. Download and install the software, then, say for example you servers ip address is 192.168.1.10

control from the web interface on any machine on

192.168.1.10:9000

Play it locally on the server with any streaming software, mplayer, cvlc etc with

localhost:9000/stream.mp3

or remotely

[http://192.168.1.10:9000/stream.mp3](http://192.168.1.10:9000/stream.mp3)

---

### Post by aeiah on 2011-07-05
MPD really is the best for the task. its a shame its crashing for you.

if you cant fix it by looking at the error logs and dont fancy a reinstall, then the squeezebox thing is probably the most similar.

another option would be to forward a music player over ssh, providing the devices you wish to control it with are able to do that. the audio would play locally (ie, out of the server) but you'd get the gui on your netbook or whatever. problem is, you'd have to install a few extra packages to install gui audio players

---

### Post by motermouth15 on 2011-07-05
Thanks aeiah-

I've been trying to fix mpd for like 6 months now and nothing has worked. I even tried posting another post about 3 months back asking for help. Its to the point now where it doesn't even give me an error, it just stops running and i have to restart the service. I really like the idea of mpd because i have a website package installed that i can control it from any browser (using jinzora). But obviously if its not going to work then I can't use it.

---

### Post by motermouth15 on 2011-07-27
I'm still not able to figure this out.

Currently I have a headless ubuntu server set up in my living room. Connected to that headless server I have a 5.1 surround sound system that plays my music. What I want to be able to do is have my server play the music locally on its own soundcard sending it out the speakers that are connected to it. I did some research on squeezebox and I can't find a way to play the music locally (not on the computer i'm currently on, but on the server).

Currently i'm trying to use Jinzora which controls MPD which sends the music out of the speakers that are connected to my server, however, MPD keeps crashing when i edit the playlist or skip songs, and sometimes when it continues down the playlist to the next song. I am wondering if there is an alternative to MPD that will be able to do that. If anyone could help me out that would amazing.

Thank you soooo much!!

---

### Post by nothingspecial on 2011-07-27
Before we go any further, I can't remember wether sound is installed by default in a server.

You do have linux-sound-base alsa-base alsa-utils?

---

### Post by motermouth15 on 2011-07-27
Yes those packages are already installed. Like I said, I already get sound, MPD just crashes whenever i change the song or it moves down the playlist a little bit. 

> **nothingspecial said:**
> Before we go any further, I can't remember wether sound is installed by default in a server.

You do have linux-sound-base alsa-base alsa-utils?

---

### Post by motermouth15 on 2011-07-29
Can anyone help me?

---

### Post by FakeOutdoorsman on 2011-07-29
How about SSHFS and MOC? I have a headless machine with speakers attached to it and can use it to play music from any other linux machine with SSHFS.

---


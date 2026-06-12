---
title: "Multiple audio streams from server"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by shearn89 on 2008-01-17
Okay, i have a (small) challenge for you all. Here is the sitch:

My dad works at a school, and has bought the license to some audio books. He wants to be able to stream these over the school network to users, so they can listen online. Learning for all!

I've set up an mpd/icecast/pitchfork set up at home, which lets me stream audio from mpd to a browser and listen to it, but i can't think of a way to stream **multiple files**.

ie:
User 1 logs onto the page, and starts playing "chapter 1". All is hunky-dory.
User 2 logs on, and pics up the stream, but wants to listen to chapter 10. He changes it.
User 1's stream is changed, and an ensuing "chapter war" causes social disaster cross - campus...


Does anyone know of a way to be able to stream 2 (preferably more) **different** audio files across a network? I've been trying to think of some similar set up that launches a new instance of something like mplayer anytime a user plays a file, but trying to code it all may be tricky... If there's a program that could do it for me i'd be waaaay grateful.

---

### Post by tgalati4 on 2008-01-17
You could set up gnump3d.  It's a simple mp3 file server.  It doesn't stream in the traditional sense, but it serves up mp3 files so anyone can listen to any chapter at any time.  

I use it to host my church recordings:

[http://wofmusic.homelinux.org:9000/](http://wofmusic.homelinux.org:9000/)

Since you are already using icecast, then logging into icecast server directly you should be able to pick up any stream for files in the icecast main directory.  I guess I don't understand the problem.

---

### Post by shearn89 on 2008-01-17
gnump3d looks like what i'm looking for - cheers.

I don't have icecast set up to stream files themselves, just to stream the audio out from mpd. Thus, it can only stream one song at a time...

---


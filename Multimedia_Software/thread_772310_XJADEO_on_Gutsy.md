---
title: "XJADEO on Gutsy"
date: 2008-04-28
forum: Multimedia Software
---

### Post by DoctorRockSo on 2008-04-28
Has anyone gotten this to work? I am in what appears to be dependency hell, between ffmpeg and XJADEO, they both have a ton of dependencies that I can't get for some reason. Synaptic won't do it, I was even having trouble getting them to work manually, because it became dependency tunnel after dependency hell. 

If anyone has had any luck with this, let me know. I am happy to show you parts of my terminal output on these ones.

---

### Post by russo.mic on 2008-07-02
I got it to work just today, actually. 

1. So, add the repos to your /etc/apt/sources.list

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main

2. sudo apt-get update
3. sudo apt-get install xjadeo

at this point, it installs, but upon running displays the message that it can't find libavformat.so.50.

4. type this:

 sudo ln -s /usr/lib/libavformat.so.52 /usr/lib/libavformat.so.50

It's also worth noteing that OpenMovieEditor can sync to jack as well.  I just got done compiling the latest libqucktime, ffmpeg, and openmovieeditor.  Things work like a dream.  Ardour and video sync has never been so easy.

enjoy your foley or adr project!

---

### Post by dchurch24 on 2009-05-05
Odd - I still get the "libavformat.so.50: cannot open shared object file: No such file" error even after the symlink.

I have searched the entire file system for that file, but it simply isn't there.

Is there another package I can install with that file in?

---


---
title: "[SOLVED] MuSE"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by paul928 on 2007-10-10
I want to use MuSE for transcoding a Shoutcast stream. I installed it and can see only options for ogg-vorbis. I think that I have every .mp3 codec installed. Does any one have any idea what I'm missing?

---

### Post by paul928 on 2007-10-14
I guess that no forum readers are familiar with MuSE.:(

---

### Post by paul928 on 2007-10-16
Well I solved the problem.Ii went to the MuSE site, [http://muse.dyne.org/](http://muse.dyne.org/), downloaded the .rpm, converted it to a .deb with alien. Now it supports .mp3 streaming. It seems that the .deb is built without .mp3 support as available from the Debian and Ubuntu  repos or from the dyne site. I'm sure that there must be a better way to do this, but since it seems that no one else has a clue, I thought that I'd mention this fix in case that someone else should have the same problem.

---

### Post by jnoreiko on 2007-11-30
I get an error about libmp3lame.so.0: no such file or directory.

---

### Post by paul928 on 2007-11-30
> **jnoreiko said:**
> I get an error about libmp3lame.so.0: no such file or directory.

i believe that you can install libmp3lame.so.0 with "sudo apt-get install liblame-dev". Also make sure that you have liblame0 installed.

---

### Post by jnoreiko on 2007-11-30
Thanks, I'll give it a shot.

Though I'm confused about the difference between that and lame -- both [http://packages.ubuntu.com/gutsy/sound/lame](http://packages.ubuntu.com/gutsy/sound/lame) and [http://packages.ubuntu.com/gutsy/libdevel/liblame-dev](http://packages.ubuntu.com/gutsy/libdevel/liblame-dev) have identical descriptions. :confused:

---

### Post by paul928 on 2007-11-30
> **jnoreiko said:**
> Thanks, I'll give it a shot.

Though I'm confused about the difference between that and lame -- both [http://packages.ubuntu.com/gutsy/sound/lame](http://packages.ubuntu.com/gutsy/sound/lame) and [http://packages.ubuntu.com/gutsy/libdevel/liblame-dev](http://packages.ubuntu.com/gutsy/libdevel/liblame-dev) have identical descriptions. :confused:

[http://packages.ubuntu.com/gutsy/libdevel/liblame-dev](http://packages.ubuntu.com/gutsy/libdevel/liblame-dev) is the development library and has the app that you need.

---

### Post by jnoreiko on 2007-12-02
Just to say that I've got it sorted.
This is what's needed:

$ sudo apt-get install liblame-dev
$ sudo apt-get install libsndfile1


(still baffled though -- if liblame is what applications need, what's in the lame package?)

---


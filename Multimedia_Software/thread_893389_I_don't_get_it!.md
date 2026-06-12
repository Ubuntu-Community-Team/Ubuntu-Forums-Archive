---
title: "I don't get it!"
date: 2008-08-18
forum: Multimedia Software
---

### Post by steviefordi on 2008-08-18
I have ffmpeg working with amr audio support (finally). I can play a file with amr encoding using VLC or even ffplay. Mplayer on the other hand, reports not having a suitable codec in libavcodec (an ffmpeg library I believe).

I have medibuntu enabled, I've un-installed and re-installed mplayer hoping it would pick up the newest ffmpeg library, but it still doesn't work.

Can anyone shed some light on this for me? (I'm using gutsy by the way).

---

### Post by wolfen69 on 2008-08-18
after uninstalling an app, make sure to do:
```
sudo apt-get clean
```and ```
sudo apt-get autoremove
``` otherwise you could just be re-installing the same app over again.

btw, what is amr audio?

---

### Post by steviefordi on 2008-08-18
Thanks, I need little tips like that. I'll give it a go.

---

### Post by steviefordi on 2008-08-19
Ok, I tried that and it still didn't work (nice tip though). Has anyone got another idea of how to solve the problem?

---

### Post by wolfen69 on 2008-08-19
do:
```
sudo apt-get install libavcodec1d
``` to see if you have the latest.

---

### Post by steviefordi on 2008-10-20
I got around to looking at this problem again and have cracked it. It appears mplayer relies on it's own static version of libavcodec, ignoring what is already on your system. To help anyone else having similar trouble here's what I did:

1. Download and install two programs that will set up the amr codecs on your machine from here: [http://www.penguin.cz/~utx/amr](http://www.penguin.cz/~utx/amr) (compilation and installation instructions included in the documentation).

2. Download the mplayer source code from here: [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) - NOT from the ubuntu repositories.

3. Follow the ubuntu 'compiling from source' instructions located here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Mplayers' configure script will detect the amr codecs installed in step 1. It will then compile them in to it's version of libavcodec and hey presto... sound from video taken on my cellphone works!

Cheers
Steve.

---


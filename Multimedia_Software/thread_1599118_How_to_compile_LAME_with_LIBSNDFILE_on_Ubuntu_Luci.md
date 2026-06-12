---
title: "How to compile LAME with LIBSNDFILE on Ubuntu Lucid"
date: 2010-10-17
forum: Multimedia Software
---

### Post by roelandp on 2010-10-17
Dear All,

I am a happy Ubuntu user, I run it on all of my servers.

A few days ago I setup a new slice, and now I want to use it to convert ULAW ([&#956;-law]("http://en.wikipedia.org/wiki/%CE%9C-law_algorithm")) WAV files into MP3's. 

If I would only install LAME this would give me an 'Unsupported data format: 0x0007'. Because LAME doesn't support ulaw encoded wav's only Linear PCM's.

I have read that one can use the Libsndfile and use it with LAME --fileio=libsndfile (or something like that) when 'MAKE'-ing Lame.  In this case because of the additional encoding library sndfile Lame can read and encode the ulaw into mp3.

I have also read another solution is to first convert the ulaw-wav into a pcm-wav with sox, and afterwards convert the output into an mp3 with lame. This seems to be a lot of extra system resources. 

**I am looking for a hands on tutorial howto wget, compile, install and run LAME with Libsndfile on Ubuntu Lucid (commandline only) so I can encode incoming ulaw files into mp3's?**

Is there anybody out here willing to help and experienced with this?

---

### Post by Yellow Pasque on 2010-10-17
I did it for you: [https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages)

EDIT: Actually, I screwed it up :\
I will redo it when I am in a better state of mind and have more caffeine. :)

---

### Post by roelandp on 2010-10-17
Thanks Temüjin!

I figured it out myself and it is working now! I'll post my steps below!

---

### Post by roelandp on 2010-10-17
Hi! I found it out myself, at least it is working right now on my Lucid!

Here is what I did, would be great if you can confirm my steps for other users who find this threat via the enginez:

Step 1. Install LibSndFile via Aptitude
```
sudo apt-get install libsndfile1 libsndfile1-dev
```

Step 2. CD into the src directory and manually wget LAME (I grabbed the 3.98.4 release) into it because we want to compile it with libsndfile
```
cd /usr/local/src 
wget http://location-of-lame-download-file-at-sourceforge.com/download
sudo tar -xvf download

```

Step 3. 
```
sudo ./configure --with-fileio=sndfile
```

Step 4.
```
sudo make
```

Step 5. 
```
sudo make install
```

That is it! 

I am  a happy camper and can now convert ulaw wav files into mp3 with LAME and the libsndfile. Oh yeah, ah yeah!

If there is a uber-sys-admin reading this tutorial, please feel free to add comments because I am rather new on server admin stuff.

---

### Post by andrew.46 on 2010-10-20
Hi roelandp,

You may be interested to know that where a copy of lame without the required option fails on these files, FFmpeg compiled against the same copy of lame cheerfully converts to mp3.

I tested with this file:

```
wget 'http://samples.mplayerhq.hu/A-codecs/uLaw/surge-2-16-B-ulaw.mov'
```

and extracted as: 

```
ffmpeg -i surge-2-16-B-ulaw.mov -acodec copy surge-2-16-B-ulaw.wav
```

to keep lame happy...

Andrew

---


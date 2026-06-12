---
title: "problems using flac"
date: 2009-03-22
forum: Multimedia Software
---

### Post by jamesclayden on 2009-03-22
Whenever i set either audiojucer or rythembox to encode of a cd it will use not use flack it will just use an alternative eg m4p ogg. I have installed flac from package manager and i am using ubuntu 8.10.

Any idea what my problem is?

---

### Post by logos34 on 2009-03-23
make sure it's enabled and the gstreamer pipeline is correct:

>edit>prefs>edit profiles>cd quality lossless (flac)>the "active?" box shouldbe checked and the pipeline look like this:
> 
audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc

---

### Post by Yerknutz on 2009-03-23
I don't have any experience with juicer or rhythmbox but am enjoying the app I was used to in Windows running in wine nicely ripping to AAC, Flac and Wmv.

[http://www.dbpoweramp.com/](http://www.dbpoweramp.com/)

---

### Post by jamesclayden on 2009-03-23
Thanks for the help.

I managed to get it working by installing the C++ library from package manager. Is there a way to get the file size a bit smaller by customizing any settings?

---

### Post by logos34 on 2009-03-23
> **jamesclayden said:**
> Is there a way to get the file size a bit smaller by customizing any settings?

if you mean the resulting flac file, I think the default is "5" on a flac scale of 0-8 (8 being the smallest, but also slower encoding speed).  

So try:
> 
audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc [COLOR="Red"]**quality=8**[/COLOR]

But remember: flac is lossless, with a size at best around 45% of the original .wav file.  You could try monkey's audio or maybe wavpack for a slightly smaller file, but you'd have to use a different ripper. (and .ape file playback = high cpu% overhead).

If space is at a premium, maybe you'd be better off with lossy format.  Personally, I use ogg rather than mp3 (-q 5 to -q 7 range, or ~160 to ~224 kbps).  can't tell it from the original

---

### Post by jayesh2605 on 2009-03-30
Same Problem here i used rythembox to encode of a cd it just uses an alternative eg m4p ogg. I have installed flac from package manager and i am using ubuntu 8.10.
pls help me out of this

---

### Post by logos34 on 2009-03-30
> **jayesh2605 said:**
> Same Problem here i used rythembox to encode of a cd it just uses an alternative eg m4p ogg. I have installed flac from package manager and i am using ubuntu 8.10.
pls help me out of this

try

sudo apt-get install ubuntu-restricted-extras

(it's a metapackage that will drag in a bunch of gstreamer stuff, including some libflac)

---


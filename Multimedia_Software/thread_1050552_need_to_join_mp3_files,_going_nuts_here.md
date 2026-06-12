---
title: "need to join mp3 files, going nuts here"
date: 2009-01-25
forum: Multimedia Software
---

### Post by jimmy the saint on 2009-01-25
I have tried every solution I can think of (short of just doing it windows).  I have a bunch of mp3's that I need to turn into one.  I have tried to CAT them, I have tried mp3wrap.  I have stripped the tags with easytag and id3v2.   

No matter what I do, the resulting file is the correct size (approx 200MB) but it is only read as being 7 minutes long (the length of the first track).  What the heck is going on?  I can't find a solution anywhere.  I figure if I can have the mp3 file's header reanalyzed, that would likely solve the problem, but I can't even find a utility for that!  I have wasted my whole sunday on this.  Anyone have a better way?

---

### Post by Jose Catre-Vandis on 2009-01-25
Are they all the same bitrate? Perhaps try soundconvertor (in the repos) to convert them all to the same bitrate and formats and have another go with cat
```
cat 1.mp3 2.mp3 3.mp3 > new.mp3
```(if I remember rightly :))

---

### Post by rattking on 2009-01-25
if all else fails try to feed them to lame

lame --mp3input input1.mp3 input2.mp3 output.mp3

---

### Post by marinepaul61 on 2009-07-13
First install Wine sudo apt-get install wine Then download BoncEnc Audio encoder a windows based program, to a folder of your choice i used documents, from [www.boncenc.org](www.boncenc.org) you will be able to download the latest version, i have version v1.0.12 and it works fine just a little quirky using ctrl hold and mouse for block selection of tracks but works after a couple of attempts. Go into the folder where you downloaded BoncEnc and right click the exe file and select open with "wine windows program loader" and install with wine, i installed into documents and selected install desktop shortcut. you will have a icon on your desktop, double click as normal to open you will get a warning screen just select trust program and away you go, you can convert any audio format to any audio format you want, to encode your mp3's to a single file select encode to a single file, go into options and select your encoder options then configure encoder. The auto update will not work so when it asks if you want to check for updates select no. I have just fineshed coverting 100GB of flac to mp3 lame at 320kbs 44100 htz

---


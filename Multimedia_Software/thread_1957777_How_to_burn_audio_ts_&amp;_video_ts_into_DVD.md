---
title: "How to burn audio_ts &amp; video_ts into DVD ?"
date: 2012-04-13
forum: Multimedia Software
---

### Post by YigalB on 2012-04-13
I have a folder including two sub folders, named audio_ts and video_ts, which were extracted from a DVD.
The DVD is supposed to have a menu that pops up when start running.

How can I burn it back into a DVD that should be run on regular home DVD player?

---

### Post by shantiq on 2012-04-13
install k9copy


```
sudo apt-get install k9copy
```


then go applications/sound and video/k9copyassistant


click on folder/find your folder with both audio and video folders/click next and disc  and next   now you see your chapters  /next pick the streams you want / copy original menus/ finish  / it will do a backup then you can burn


that is it:KS   best of luck

---

### Post by YigalB on 2012-04-13
> **shantiq said:**
> install k9copy

```
sudo apt-get install k9copy
```

then go applications/sound and video/k9copyassistant

click on folder/find your folder with both audio and video folders/click next and disc  and next   now you see your chapters  /next pick the streams you want / copy original menus/ finish  / it will do a backup then you can burn

I followed the instructions, the software started running but it crashed before it ended.
The DVD that the files were extracted from was supposed to have a menu that runs endlessly. 
My end target is to create such endless DVD from these files
is there a way to recover?

---

### Post by shantiq on 2012-04-13
sorry Yigal do not understand this

> the files were extracted from was supposed to have a menu that runs endlessly


sorry it crashed .  i do not know what to say now    no other ideas from me someone else might turn up:KS

---

### Post by YigalB on 2012-04-13
> **shantiq said:**
> sorry Yigal do not understand this
sorry it crashed .  i do not know what to say now    no other ideas from me someone else might turn up:KS

Somehow I missed few words. OOps, sorry.

So here is the sequence:
1- I got a DVD media that includes a video with menu that runs endlessly (i.e. in a loop)on standard DVD player
2- I extracted that DVD media and got a folder with AUDIO_TS and VIDEO_TS sub folders
3- From unknown reason the original DVD was destroyed, and now I have the digital media.

My target now is to recreate the original DVD media, so it could play endlessly on standard DVD player.

Any idea would be appreciated.

---

### Post by Steeperton on 2012-04-13
try mksiofs

```
 mkisofs -dvd-video -o ~/dvdname.img /PATH/TO/FOLDER/ 
```

If that works, any DVD burner will burn the ISO.

---

### Post by YigalB on 2012-04-13
> **Steeperton said:**
> try mksiofs

```
 mkisofs -dvd-video -o ~/dvdname.img /PATH/TO/FOLDER/ 
```

If that works, any DVD burner will burn the ISO.

The program itself worked fine, I got image file and burn the DVD.

The problem is that I don;t get the menu, nor in my PC, nor in the DVD player. 
When I look inside the DVD, the files are there, so I don;t understand what went wrong.

Is there a way to analyze the DVD content? to see if the menu is good and valid, and if it is actually directing the DVD player to run in endless loop?
Or, is there a way to strip this DVD into MPEG, and create a playable DVD out of it?

---

### Post by Steeperton on 2012-04-13
Try opening the directory in VLC (I know there's an option to play directory in there, not sure about other programmes). 

It could be that when ripping the DVD, you've removed the menu, somehow.

---

### Post by lemik on 2012-04-24
Here is the answer: 

[http://ubuntuforums.org/showpost.php?p=9557968&postcount=10]("http://ubuntuforums.org/showpost.php?p=9557968&postcount=10")

---

### Post by perspectoff on 2012-06-12
I have been having the same problem for some time (including in Oneiric), but the problem for me occurs at the 3.8 GB mark on regular DVDs (DVD-R type) as well, not just on D/L DVDs.

I never had these problems in Lucid (I went directly from Lucid to Oneiric).

I have no problem burning DVDs less than 3.8 GB, so the problem isn't my drive (which is the same one I've used since Hardy). The problem occurs with Brasero, k3b, k9copy, or Gnomebaker, so the front-end seems to be irrelevant.

The symptoms are freezing when burning anything to DVD (data of any kind) when burning reaches the 3.8 GB mark, no matter if I use Brasero, Gnomebaker, k3b, or k9copy. Alternately, burning might complete, but the disk is unusable or unreadable (especially the data written last). Finally, the burning program may just crash without explanation, or with the mysterious "error 254." 

My suspicion is also that it is related to genisoimage (and growisofs for D/L media) and/or wodim that comes with cdrkit -- I think they are not properly handling large amounts of data around the 4 GB mark on DVDs. If I'm not mistaken, smaller amounts of data are handled by wodim (or cdrecord when installed) and large amounts of data (around 4 GB or more) are preconfigured by genisoimage or growisofs (or mkisofs if installed) before being written by wodim.

Debian/(K)Ubuntu replaced cdrecord with wodim and mkisofs with genisoimage and growisofs (when the cdrkit vs. cdrtools licensing war started), creating symbolic links (so that front-end programs are fooled into using wodim for cdrecord and genisoimage and growisofs for mkisofs).

It takes a little work to go back to the real cdrtools (instead of cdrkit) and use the real mkisofs instead of genisoimage, and cdrecord instead of wodim, as this guy did by changing symbolic links:

 [http://ubuntuforums.org/showthread.php?t=852085](http://ubuntuforums.org/showthread.php?t=852085)

Brandon Snider's .deb package for cdrecord installs ok, but not the mkisofs package, as there are lots of errors and "removal dependencies" when genisoimage is removed, which cripples the system. 

[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

Alternatively, perhaps the problem is not with cdrkit but has something to do with this recent (Dec 2011) update to libdvdread (i.e. maybe the problem wasn't fixed completely/correctly)?

libdvdread (4.2.0-1ubuntu3) precise; urgency=low

* Add 103-iforead-tt-srpt-pointerfix.patch: Fix read/write beyond end of
an array due to using a length value taken from the DVD, which can
exceed the allocated size, causing a segmentation fault.
(LP: #894170)

Whatever the root of the problem, I currently cannot burn DVDs past the 3.8 GB limit in (K)Ubuntu.

---


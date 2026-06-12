---
title: "Mp3 cd creator/transcoder?"
date: 2007-11-12
forum: Multimedia Production
---

### Post by dragon2611 on 2007-11-12
Does anyone know program that can create mp3 cds

I know I could use a k3b to just burn the files, but ideally I want something thats a bit smarter than that, i'd like to be able to just drop a Flac file into it and have it transcode it to mp3 before it gets burnt.

Most of my music is mp3 but I've recently started using Flac, problem is my car cd player doesn't do flac but it can play mp3/wma files so I was wandering If its possible to get the pc to auto transcode the files before burning to cd.

---

### Post by disturbed1 on 2007-11-13
I'm not aware of any software that does that. Not even sure if the same thing is present in windows.

A simple
```
lame -b 192 *.flac
```Will encode all files that end in .flac to mp3 format with a bitrate of 192. You can play around with the setting to change them to what you want. If you have 01.flac 02.flac it will encode the files to 01.mp3 02.mp3. However it will not retain the ID3 tags.

If you prefer a GUI, put all of your FLAC files in a seperate directory and run Sound Converter (available through synaptic). This will also retain the ID3 tags.

---

### Post by UK-Wobbie on 2008-03-23
> **dragon2611 said:**
> Does anyone know program that can create mp3 cds

I know I could use a k3b to just burn the files, but ideally I want something thats a bit smarter than that, i'd like to be able to just drop a Flac file into it and have it transcode it to mp3 before it gets burnt.

Most of my music is mp3 but I've recently started using Flac, problem is my car cd player doesn't do flac but it can play mp3/wma files so I was wandering If its possible to get the pc to auto transcode the files before burning to cd.

If you like to make a Mp3 CD, The only thing you need to do is make a date CD.
Put all you Mps on to a CD and burn it!
Put it in in to you Mp3 CD player and it will play :)

---


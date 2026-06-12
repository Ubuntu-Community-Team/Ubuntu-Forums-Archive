---
title: "kid3- insert track number"
date: 2009-03-26
forum: Multimedia Software
---

### Post by ave2 on 2009-03-26
Hi I just installed the kid3 application, and cannot for the life of me figure out how to automatically insert track numbers into the title of the id3 tag- this is important because im listening to audio books that need to play in sequence, and my mp3 player automatically sorts by id3 title- so for example I want it to read 01-The Hobbit, but each track obviously have the corresponding track number

---

### Post by ufleisch on 2009-03-26
To get the track number from a file name (e.g. 01-The Hobbit.mp3) into the tags, just click "From Filename". To construct the filename from the tags, just click "From Tag 1" or "From Tag 2". You can set the format in the "Format" line edit, e.g. "%{artist} - %{album}/%{track}-%{title}". Maybe you can download a newer Kid3 release from [http://kid3.sourceforge.net](http://kid3.sourceforge.net), as these functions have been improved recently.

---


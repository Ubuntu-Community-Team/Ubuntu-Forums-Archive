---
title: "get_iplayer fails to convert flv (on 12.04 via linuxonandroid"
date: 2012-11-22
forum: Multimedia Software
---

### Post by Dafydd on 2012-11-22
Hi,
I've finally got get_iplayer working on my phone! It's great as I can download BBC radio to listen to but get_iplayer won't convert the flv to mp3.

Any one know what dependencies I need?

The Ubuntu installed is 12.04.

I can't get the linux for android thing to install mediubuntu (with the key).

Any help would be much appreciated.

---

### Post by ron999 on 2012-11-22
> **Dafydd said:**
> ... but get_iplayer won't convert the flv to mp3.

The Ubuntu installed is 12.04.
Hi
Update to get_iplayer v-**2.82**
(Look for Jon Davis PPA)

Then use commands like these...
For m4a files:-
```
get_iplayer --type=radio --pid=b01ntjpz
```
For mp3 files:-
```
get_iplayer --type=radio --pid=b01ntjpz --aactomp3
```

---

### Post by evilsoup on 2012-11-22
get_iplayer uses ffmpeg/avconv to convert files; I can't remember if it is counted as a dependency, since it isn't *strictly* needed. Try installing ffmpeg.

---


---
title: "open m3u file in terminal"
date: 2010-03-22
forum: Multimedia Software
---

### Post by 8301 on 2010-03-22
Yellow

I an trying to open a m3u file from the terminal in audacious2.
The goal is to play music with the remote and switch between different playlists.

When I write 

```
htpc@htpc:~$ audacious2 /home/htpc/Music/sebastian.m3u

```
I get
```
** (audacious2:3209): WARNING **: Could not open file:///home/htpc/Music/Sebastian/Trance/Greg%20Downey%20-%20Global%20Code%20(Scot%20Project%20Remix).mp3 for reading or writing: Error opening file: No such file or directory
Unable to read from file:///home/htpc/Music/Sebastian/Trance/Greg%20Downey%20-%20Global%20Code%20(Scot%20Project%20Remix).mp3, giving up.
Segmentation fault
```

Audacious is trying to open the last played file instead of my playlist file

---


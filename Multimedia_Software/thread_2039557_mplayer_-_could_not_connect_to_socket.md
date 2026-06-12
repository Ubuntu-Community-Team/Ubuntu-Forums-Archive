---
title: "mplayer - could not connect to socket"
date: 2012-08-09
forum: Multimedia Software
---

### Post by bill-lancaster on 2012-08-09
This was working yesterday!

$> mplayer -playlist playlist1.txt

but now get the following message:-

"MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

/home/bill/Music/Library/000026.mp3.002.mp3
/home/bill/Music/Library/000026.mp3'brary/000002.mp3
/home/bill/Music/Library/000026.mp3.ary/000002.mp3"

Note that the contents of the playlist file are:-

/home/bill/Music/Library/000002.mp3
/home/bill/Music/Library/000022.mp3
/home/bill/Music/Library/000532.mp3
/home/bill/Music/Library/000026.mp3

Any help would be much appreciated

---

### Post by bill-lancaster on 2012-08-10
I have found the answer.

The playlist was constructed from my own programme and each line was terminated with only ascii(13), it needs ascii(13) & ascii(10).

---

### Post by ads52 on 2012-08-10
As an aside: if you want to get rid of the annoying lirc message simply place the following in *$HOME/.mplayer/config*:

```
lirc=no
```Unless of course you are trying to use a remote control with MPlayer :).

---


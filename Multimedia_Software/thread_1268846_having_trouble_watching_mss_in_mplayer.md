---
title: "having trouble watching mss in mplayer"
date: 2009-09-17
forum: Multimedia Software
---

### Post by Tadcrazio on 2009-09-17
I'm taking an online course and it requires me to watch a movie and its in mms.. I looked around and i saw a command i can type along with the address of the video and mplayer would play it. I am still having trouble it says its a bad command in the terminal. Any help would be appreciated. the link to the video is [http://www.learner.org/vod/vod_window.html?pid=338](http://www.learner.org/vod/vod_window.html?pid=338)

---

### Post by mc4man on 2009-09-17
If you have the mozilla-mplayer plugin installed they'd probably play fine thru browser with a 'next video' button also available, otherwise one way

 ```
mplayer -cache 1024 -playlist   http://www.learner.org/vod/asx/seattle/Economics_USA_0[COLOR="Red"]1[/COLOR].asx
```

 ```
mplayer -cache 1024 -playlist   http://www.learner.org/vod/asx/seattle/Economics_USA_0[COLOR="Red"]2[/COLOR].asx
```

ect.ect.

Not a very high quality video, don't make the video to large

another way would be 
 ```
mplayer -cache 1024  mms://media.scctv.net/annenberg/Economics_USA_0[COLOR="Red"]1[/COLOR].wmv
```

edit:
it looks better in vlc ...?, the output posted below
```

vlc http://www.learner.org/vod/asx/seattle/Economics_USA_01.asx
```

> doug@doug-laptop:~$ vlc [http://www.learner.org/vod/asx/seattle/Economics_USA_01.asx](http://www.learner.org/vod/asx/seattle/Economics_USA_01.asx)
VLC media player 1.0.2-git Goldeneye
LibVLC has detected an unusable buggy GNU/libc version.
Please update to version 2.8 or newer.
[0x8051140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x81c0d60] access_mms access: selecting stream[0x1] audio (80 kb/s)
[0x81c0d60] access_mms access: ignoring stream[0x2] audio (33 kb/s)
[0x81c0d60] access_mms access: ignoring stream[0x3] audio (17 kb/s)
[0x81c0d60] access_mms access: selecting stream[0x4] video (216 kb/s)
[0x81c0d60] access_mms access: ignoring stream[0x5] video (96 kb/s)
[0x81c0d60] access_mms access: ignoring stream[0x6] video (41 kb/s)
[0x81c0d60] access_mms access: connection successful
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1


---


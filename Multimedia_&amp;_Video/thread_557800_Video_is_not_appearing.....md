---
title: "Video is not appearing...."
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by pranshu on 2007-09-23
hey i recently installed vlc and few codecs to make my movie player work. Just after i installed it it was working fine. But now the picture only appears when i just start the video... the next moment picture disappears and only sound remains... the video is also visible when i resize the window... but again the same thing happens... the moment it shows the next moment its gone... i'm facing this problem only with vlc and totem BUT surprisingly gXine player is working fine... so right now i'm only playing videos with gXine.... Please help .... i know the video is working but its not showing....

---

### Post by Gremlinzzz on 2007-09-23
How to fix black windows during video playback

    * There is a workaround to this bug by changing the video output device on your video player. 

    * For gstreamer-dependent players (Totem, etc.): 

gstreamer-properties
Video-->Default Video Plugin: X Window System (No Xv)

Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).

    * For VLC player(if installed): 

VLC-->Settings-->Preferences
Video-->Output modules-->Advanced: X11

    * For MPlayer (if installed): 

Mplayer-->Right-click on the screen-->Preferences
Video-->Available Drivers: X11 (XImage/Shm)

Some users report that MPlayer may not be able to show videos in full screen.

    * For Xine player (if installed): 

Xine-->File-->Configure-->Preferences
experience_level: Master Of The Known Universe
Video-->Driver: xshm 

    * For RealPlayer (if installed): 

RealPlayer-->Tools-->Preferences
Hardware-->Deselect: Use XVideo
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by shishirmk on 2007-09-23
its also a common bug if you have installed compiz-fusion or beryl..

---

### Post by fr33d1v3r on 2007-09-26
Altough I did not ask the question, but it helped me to solve the same problem. Thanx a lot from a newbie.

---


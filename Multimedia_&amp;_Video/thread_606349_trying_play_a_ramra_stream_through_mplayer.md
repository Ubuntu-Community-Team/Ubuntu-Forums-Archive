---
title: "trying play a ram/ra stream through mplayer"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by ridetheteapot on 2007-11-07
I can listen to mp3 or ogg streams fine, but ram streams are not playing (haven't found a wma stream to try)
i have w32codecs installed and use mplayer.
mplayer -playlist ram.ram seems like its working (there are no error messages and mplayer continues to run until stopped) but there is no sound.

[http://www.wnyc.org/shows/bl/episodes/2005/03/24](http://www.wnyc.org/shows/bl/episodes/2005/03/24)
is where the streams are found.

all the newer shows from wnyc are in mp3 form but i was trying to listen to this older one.

if its a matter of installing gstreamer or realplayer i will have to skip it i guess, but i thought that w32codecs would stream a ra file


total side note. anybody know how to stop an' mplayer -dumpstream' stream recording after a certain amount of time? or dump the pid into a file so crontab can kill it later (without killall mplayer). -endpos doesn't word when recording a stream.

---

### Post by MrFSL on 2007-11-07
Not sure about ram streams - but this might help:

[http://www.real.com/linux/](http://www.real.com/linux/)

---

### Post by ridetheteapot on 2007-11-08
yea, i'm sure that would work fine, but i swore never to use realplayer again ayears ago cause it totally invades windows running all these processes, i can't imagine what it would be like if it acts the same way on linux

---


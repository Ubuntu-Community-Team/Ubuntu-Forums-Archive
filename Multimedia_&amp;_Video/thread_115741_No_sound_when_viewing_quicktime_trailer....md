---
title: "No sound when viewing quicktime trailer..."
date: 2006-01-11
forum: Multimedia &amp; Video
---

### Post by mmcmonster on 2006-01-11
I was able to view the trailers at [www.apple.com/trailers](www.apple.com/trailers) in firefox without a problem.  I am using mplayer to view quicktime movies.  Yesterday I tried to view the following trailer, and it had no audio:

[http://www.apple.com/trailers/wb/harry_potter/thegobletoffire/small.html](http://www.apple.com/trailers/wb/harry_potter/thegobletoffire/small.html)

I downloaded the trailer and tried to run it off my desktop, and it gave the following error: "Cannot find codec for audio format 0x32d4451."

Any ideas?  I googled for the audio format number and didn't find anything. (!!!)

BTW, the other quicktime videos and other videos on my computer seem to play properly.

---

### Post by Thirsteh on 2006-01-11
Try going to mplayers [website](http://mplayerhq.hu) and fetch their "essential codecs" package, put it in /usr/lib/win32 (have to make the folder with sudo mkdir /usr/lib/win32) - and make a symlink to that folder called codecs, with this command:

sudo ln -s /usr/lib/win32 /usr/lib/codecs

Good luck.

---

### Post by mmcmonster on 2006-01-11
/usr/lib/codecs already exists, and has a large number of codecs already in it.  Should I create a link inside that directory (/usr/lib/codecs/win32 -> /usr/lib/win32 )

---

### Post by mmcmonster on 2006-01-11
That worked, by the way. :-)

Thanks for the quick reply.

---

### Post by Sabrage on 2006-07-22
when i try to copy the files to the usr/lib/win32 directory it says i'm not allowed?

---

### Post by Sabrage on 2006-07-22
tried this commad:```

sudo cp -p /home/myusername/essential-20060611 /usr/lib/win32
```
and got this:
```
cp: omitting directory `/home/myusername/essential-20060611'
```

:confused:

---

### Post by Sabrage on 2006-07-22
hey i just noticed i'm in the wrong forum! omg! i have ubuntu 6.06 not 5.10! oh well....

---


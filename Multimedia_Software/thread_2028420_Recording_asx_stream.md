---
title: "Recording asx stream"
date: 2012-07-18
forum: Multimedia Software
---

### Post by chatln on 2012-07-18
I have been trying to record these lectures using  mplayer's -dumpsream option but it only records what seems just a frame. These videos does not work properly in firefox so I am planning to upload them to youtube for Go players using Linux :) Can you suggest me a way to record them.

Here is the link:
[http://www.wbaduk.com/fileupdown/lecture_movie/intermediate-01c.wmv.asx](http://www.wbaduk.com/fileupdown/lecture_movie/intermediate-01c.wmv.asx)

Thank You.

---

### Post by P1ta on 2012-07-18
```

apt-get install mimms
mimms mms://movie.cyberoro.com:7002/nihonkiin/Cyberoro/lecture_eng/intermediate-01c.wmv

```

---

### Post by chatln on 2012-07-18
> Connection reset by peer
Could not read packet header: Connection reset by peer
libmms error:/usr/lib/python2.6/dist-packages/libmimms/core.py:245: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  print >> sys.stderr, "libmms error:", e.message
libmms connection error I got this error but i have managed to record using vlc thanks to your mms link.

---

### Post by P1ta on 2012-07-18
You need to update your Python to Python 2.7.

---


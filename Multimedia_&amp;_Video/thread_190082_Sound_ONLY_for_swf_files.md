---
title: "Sound ONLY for swf files?"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by tjacobs on 2006-06-05
After upgrading to dapper and running automatix I only have sound for flash files. How can I get my sound back for everything else?

---

### Post by tjacobs on 2006-06-08
After playing around a bit more, I think the problem may be that firefox is not freeing up the sound device. This guess based on the following message from LastFM player:
RtApi: no devices found for given stream parameters:
    RtApiAlsa: pcm capture open (hw:CMI8738,0) error: Device or resource busy.
    RtApiAlsa: pcm device (hw:CMI8738,1) doesn't handle input!
    RtApiAlsa: pcm capture open (hw:CMI8738,2) error: Device or resource busy.

Is my guess reasonable? And, if so, how do I fix the problem?

---


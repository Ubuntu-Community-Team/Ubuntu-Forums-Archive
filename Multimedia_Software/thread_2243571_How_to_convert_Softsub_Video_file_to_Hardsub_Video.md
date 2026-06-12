---
title: "How to convert Softsub Video file to Hardsub Video file?"
date: 2014-09-09
forum: Multimedia Software
---

### Post by blackvm on 2014-09-09
How to convert Soft-sub Video file to Hard-sub Video file ?



  I have many mkv video files but I can't watch this videos because the  subtitles don&#8217;t appear so I want to convert this files to Hard-sub  without changing subtitles fonts or anything in this videos.

---

### Post by FakeOutdoorsman on 2014-09-11
See [Adding subtitles to a video](http://ubuntuforums.org/showthread.php?t=2192097&p=12868641&viewfull=1#post12868641).

---

### Post by blackvm on 2014-09-13
Thanks
OK, that appears to have worked, but there is another problem : the size of the file went from 379 mb to 168 mb so the quality is changed
So thr question is: How to convert my videos without  losing video or audio quality ?

---

### Post by FakeOutdoorsman on 2014-09-14
You can use a [lossless encoder](https://trac.ffmpeg.org/wiki/Encode/H.264#LosslessH.264), but it will create a huge file and it may not be playable by whatever device you're using.

Otherwise, since making hardsubs requires that you re-encode, you may have to accept some quality loss. Read about the [-crf](https://trac.ffmpeg.org/wiki/Encode/H.264#crf) option if you're outputting H.264 video.

---

### Post by blackvm on 2014-09-19
Thank you very much

---


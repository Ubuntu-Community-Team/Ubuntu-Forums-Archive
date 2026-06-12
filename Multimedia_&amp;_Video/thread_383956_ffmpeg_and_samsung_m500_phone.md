---
title: "ffmpeg and samsung m500 phone"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by smooth_b on 2007-03-13
I just wanted to share with everyone the syntax that I use to convert mpeg files to a 3gp format that will work on my samsung m500 phone.  Just in case someone else cares to know. 


 ffmpeg -i video_file.mpg -s qcif -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y video_file.3gp

---


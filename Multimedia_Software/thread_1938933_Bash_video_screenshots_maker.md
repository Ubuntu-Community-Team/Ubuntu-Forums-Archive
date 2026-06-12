---
title: "Bash video screenshots maker"
date: 2012-03-10
forum: Multimedia Software
---

### Post by rokixz on 2012-03-10
Hello,

I need to make png format screenshots on all videos. And the problem is that there are about 300 files in totals. What I want to do is to take a single snapshot of the movie frame 1:50 minute and put same name as video but diferrent extension (png). I know I should make a bash script for this, but any suggestions which application should I use? Or even better way maybe you did something same and can share the script? I use OGG theora format to all my videos.

Thanks for help, hope I'll be responded here :)

---

### Post by rokixz on 2012-03-10
OK, found how to do it with ffmpeg. Anyway, sorry for flooding forum, but if it's interesting here's the web page:
[http://code.coneybeare.net/how-to-generate-png-screenshots-using-ffmpeg](http://code.coneybeare.net/how-to-generate-png-screenshots-using-ffmpeg)

Thanks :)

for k in $(ls -1 | sed 's/\(.*\)\..*/\1/'); do avconv -ss 00:1:50 -t 1  -i $k.ogg -f mjpeg images/$k.png; done
Does the trick :)

---


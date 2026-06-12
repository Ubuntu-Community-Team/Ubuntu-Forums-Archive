---
title: "flv to video"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by thedevilisbad on 2008-02-16
Is there a program out there to covert .flv's to other video formats? I'd really like to put some video's on my ipod so I need mp4. Actually anything would do cause I could you VLC to convert between formats, it won't work for flv (I tried :( )

---

### Post by Rhubarb on 2008-02-16
Get ffmpeg:
```
sudo aptitude install ffmpeg
```

Then use this command to convert the flv file to mp4:
```
ffmpeg -i inputfile.flv -acodec copy -vcodec mpeg4 outputfile.mp4
```

Altrenatively, you can follow this guide:
[http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946)

You should also be able to use mencoder to do this too.

---

### Post by stooshbunutu on 2008-03-11
for a GUI to ffmpeg try winff from [http://www.biggmatt.com/winff](http://www.biggmatt.com/winff)

---


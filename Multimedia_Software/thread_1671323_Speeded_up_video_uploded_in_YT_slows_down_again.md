---
title: "Speeded up video uploded in YT slows down again"
date: 2011-01-19
forum: Multimedia Software
---

### Post by Kangarooo on 2011-01-19
I cut a piece from movie using VLC while playing speed up
Sometimes result is good sometimes sound is scratcy.

Thouse times its bad i tryd VLC record normal speed then in Avidemux. But it cant import thouse witch are recorded from VLC
So i tryd whole video import in Avidemux and selected piece i need then in filters **Resample FPS** and set my FPS
And codex didnt tryd all but first 3 gave some errors and H.263 also but last was ok its MPEG-4 AVC
So i save and ... video isnt faster..

WHWHAyaywwayawAW??
7689ui0o-prt9i8e8r6er8u9iser ou98ar 9wea oi fu908yc4w
Is there any better codex to choose in programm or better program?
Or just one command that does work for all codex like flv avi mpeg and only exports new video with desired fps?

Update:
Tryd ffmpeg found that i can only make more fps in video witch doesnt mean it will be faster but more quality.
Found yuvfps witch can be piped in between opening and extracting video command but didnt actually gave sound corretly at least for me.
ffmpeg -i video.avi -f yuv4mpegpipe - | yuvfps -s 120:1 -r 120:1 | ffmpeg -f yuv4mpegpipe -i  - -b 28800k  slow.avi
from
[http://linuxers.org/tutorial/how-slowdown-or-speed-video-using-ffmpeg-and-yuvfps](http://linuxers.org/tutorial/how-slowdown-or-speed-video-using-ffmpeg-and-yuvfps)
Then found mencoder witch gives error messeges and helps fixing and my fixed command was working but giving chipmunk sound so at least closer and its
mencoder Klimnjaro\ Robot.avi -oac mp3lame -srate 8000 -ovc lavc -speed 1.3 -o a.avi

---


---
title: "ffmpeg help"
date: 2012-10-03
forum: Multimedia Software
---

### Post by S_p_or_t_o on 2012-10-03
i'm using a dvd/divx player to feed into a menu board. i have a new video and i'm trying to convert a .mov file into a xvid .avi

the trouble is the video looks terrible after i convert it.


using winff, i have a preset with the following options
```
-f avi -r 29.97 -vcodec libxvid -vtag XVID -s 1280x720 -aspect 16:9 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4m -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2
```

2 pass doesn't seem to make a difference.

using ubuntu studio 12.04 x64

any advice would be appreciated.

---


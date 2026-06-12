---
title: "mencoder avi to dvd problems"
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by kasemodz on 2006-10-13
Hi, I'm trying to convert this avi file into mpeg2, then using dvdauthor to make the dvd. Now I used mencoder on this as stated in their documentation. Here is the orignal avi file description.

> VIDEO:  [XVID]  608x336  16bpp  23.976 fps  982.1 kbps (119.9 kbyte/s)


Here are the mencode specs to convert the file into mpg.

> mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:480,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:acodec=ac3:abitrate=192 -ofps 30000/1001 -o 1.mpg 1.avi


Can someone plz help?

I took this right from mplayer documentation. It converted the video, but the total play time now is about 40 min and its suppose to be hr and a half. It plays the whole movie, but the frame rate is very slow, when viewing on the tv, i could see the frame moving from one to another.

---

### Post by pay on 2006-10-13
NTSC use 30fps. Maybe that's the problem. You might get more help with these sorts of problems on doom9.net

---


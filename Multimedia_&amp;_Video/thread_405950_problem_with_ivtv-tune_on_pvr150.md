---
title: "problem with ivtv-tune on pvr150"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by milk_inc on 2007-04-10
hi there, i m new here, well  i m having problem with my tv tuner well before works fine i can set channet and see tv on vlc or mplayer well suddenly appear this message when i want to switch channel using hte command ivtv-tune -c(number of channel) well appear this error on console, ioctl VIDIOC_S_FREQUENCY failed.
I'm using Feisty my tv tuner works fine coz i tested on windows too, the problem appear before but i just restart the pc and works fine i restart too even turn off and ntohing happend my tv tuner is pvr150 thanks for the help i hope u can help me :)

---

### Post by rsambuca on 2007-04-23
I'm having the same problem now on feisty 64-bit.  It was working perfectly for a while, but suddenly today, I got the same error message when I try to tune the channel.  For some reason, it now says that I have no /dev/video0 device!  It works fine in XP, Vista, and feisty 32-bit.

I was installing a ton of stuff on the weekend, though, so that may have something to do with it.

If any one has ideas, please let me know and I can post whatever outputs you need.

Thanks in advance.

---

### Post by rsambuca on 2007-04-27
I lost the tuner in Feisty 32bit too.  Turns out my tuner changed from /dev/video0 to /dev/video1.  I have no idea why, or what I did, but at least it is working now.

---


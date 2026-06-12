---
title: "Problem with TV-out and strange solution"
date: 2008-05-07
forum: Multimedia Software
---

### Post by Estepario on 2008-05-07
Hi everyone, 

i've been trying to connect my laptop with the TV with a S-video- RCA cable.
I follow the instruction from:

[http://ubuntuforums.org/showthread.php?t=600091](http://ubuntuforums.org/showthread.php?t=600091)

It works fine, but a couldn't see full screen videos in TV.
i was using smplayer to see videos, but then i tried with xine but no luck with that.

Then the strange thing happens. I put smplayer in pause, and opened xine, and then magically a could see my full sceen videos with xine in the TV. But if i close smplayer, then i can't see videos.

Anyone have a explanation???
How can i solve the problem to see the video with only one program open???

By the way, i have a dell inspiron 600m with an ATI Randeon Mobile 9000 and i'm using Ubuntu 7.10

---

### Post by CarpKing on 2008-05-07
I'm not sure why that works, but i'd recommend installing gxvattr.  Switch XV_OUTPUT_DEVICE from 0 to 1 and you should be able to see video.

---


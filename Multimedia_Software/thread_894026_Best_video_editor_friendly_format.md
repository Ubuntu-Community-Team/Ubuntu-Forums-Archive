---
title: "Best video editor friendly format?"
date: 2008-08-18
forum: Multimedia Software
---

### Post by s3a on 2008-08-18
I am trying to learn video editing and I would like to know which format is the best to use with Cinelerra-CV. I have a video file with the extension .avi but I heard this is not good or the best to use. So what would I need to use instead and how would I convert it?

Any help would be appreciated!
Thanks!

---

### Post by mateuszbaranski on 2008-09-05
Dear  s3a
*extension .avi* means nothing really at all.
In file that has an extension .avi you could have movie DivX coded, you could have movie Xvid coded, and many others. Avi AFAIK is just the container for video and audio streams.

You could check what kind of video is inside your AVI file using mplayer:
```
mplayer -identify yourmovie.avi
```

If you don't have mplayer just type:
```
sudo apt-get install mplayer
``` 

Back to the best format in Cinelerra. From documentation you could read that the "native" format of Cinellerra is DV in Quictime container (.mov extension - in Render menu called "Quictime for linux") which is quite odd. I personnaly use DV in DV container - in render menu called "Raw DV". Why? Because I use miniDV camcorder. 
Cinelerra handles also standard MPEG2 codecs (from DVD), which come from ripped DVD.
I hope it clarifies something for you.

---

### Post by Crafty Kisses on 2008-09-05
I personally like Kino.

---

### Post by Eastree on 2008-10-26
I just installed Kino, but it will not even read the video I would like to edit.  I know I should start a thread, but since the one I *did* start is being ignored, I'll just reply to others.

Also, though I've added the repository to the list for Cinelerra, it still does not show up in the list.

---


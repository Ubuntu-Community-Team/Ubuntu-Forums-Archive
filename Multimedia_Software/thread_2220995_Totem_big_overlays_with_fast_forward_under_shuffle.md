---
title: "Totem big overlays with fast forward under shuffle mode"
date: 2014-04-30
forum: Multimedia Software
---

### Post by Briga on 2014-04-30
Hi, I wonder if anyone has the same issue, if it's a bug (I suppose) or what. 

Running Ubuntu 14.04 64 bit with Totem 3.10.1

To replicate the issue set Totem in Shuffle Mode (otherwise it won't happen), then load some video files in the playlist. 
The first one plays fine and if you go forward (or backward) with any arrows or combination (Shitf+ and so on) it works well. 
When it goes to the next random file in the playlist and you skip forward (i.e. right arrow) a huge symbol of FF overlays the screen covering the movie for few seconds!

It's quite annoying and I wonder how to disable it. 

Thanks

---

### Post by gregconquest2 on 2014-04-30
It is not just you. When I play videos in "Videos", using the arrow keys to go forward or backward puts a huge, HUGE arrow overlay over the video. It lasts about a half second before it fades. It makes it difficullt to rapidly search for anything in the video.

---

### Post by Briga on 2014-05-05
I suppose is a bug then. 
A workaround is to use VLC as a player but of course not a fix......

---

### Post by monkeybrain20122 on 2014-05-06
Just install Smplayer, Vlc or mpv. Totem sucks in general, I have removed it.

---

### Post by carlos47 on 2014-05-16
Yeah, it's SOOO annoying (That, and the fact that you can't easily modify how much you can go forward or backward with hotkeys (WHY did they make skip backward less than skip forward?).

I've tried and downloaded about 10 other video players, and GNOME MPlayer and SMPlayer are the best... as well as a couple others...
But in terms of speed, Totem is by far the fastest. It loads the next video *immediately* and overall behaves very quickly.

I'm also using Ubuntu 14.04. I hope they fix it soon.

---

### Post by Briga on 2014-11-19
In the end I understood they will never fix it. But there is a workaround!

If you follow this advice [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1309605/comments/18](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1309605/comments/18) and patch it yourself. 

I did it and it worked, fixing the issue.

---

### Post by Mn1945786 on 2015-01-21
Can you please tell me in which file (with full path) should I paste the above code?

---

### Post by Briga on 2015-01-21
> **Mn1945786 said:**
> Can you please tell me in which file (with full path) should I paste the above code?

The full path is in the article:
totem-3.10.1/src/totem-object.c

based on where you uncompressed the downloaded file.

Bye

---


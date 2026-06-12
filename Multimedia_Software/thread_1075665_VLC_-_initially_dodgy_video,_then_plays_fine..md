---
title: "VLC - initially dodgy video, then plays fine."
date: 2009-02-20
forum: Multimedia Software
---

### Post by musther on 2009-02-20
Same problem on both my netbook and desktop - both running Intrepid, both using compiz, both VLC from repos, version 0.9.4 Grishenko.

When I open an avi video with VLC, the program opens and audio begins playing.

On my desktop, the video area remains black, or sometimes displays a single frame from the first couple of seconds.  If I hit pause, and then play again, or skip forward or back a little, it starts working.  

On the netbook, I get an early frame, frozen on the screen.  I hit pause, then play, then get moving video, but scrambled until a scene change or something which requires a complete image refresh, then it works.

I've tried using the different video output modules, but get the same issue with all of them.

Any thoughts?

---

### Post by Mercury_Alpha on 2009-02-20
Sometimes you'll get performance issues when attempting to play large video files, if you don't have a lot of free memory or if your hardware is a little older. You may also want to try disabling video overlay in your xorg.conf file. That entry is listed in the "Device" section of the file. But make a backup of xorg.conf before you make any changes to it. [This is an example of one version of the file]("http://nozell.com/examples/xorg.conf-fglrx.20060621"), if you haven't seen it before.

---

### Post by digitalbenji on 2009-02-20
I think if you don't have that fast a computer that it also depends where you are playing the file from.  I find that files play much quicker for me off my hard drive then off an optical disc drive or external USB device.

---

### Post by sonicb00m on 2009-02-20
> **musther said:**
> Same problem on both my netbook and desktop - both running Intrepid, both using compiz, both VLC from repos, version 0.9.4 Grishenko.

When I open an avi video with VLC, the program opens and audio begins playing.

On my desktop, the video area remains black, or sometimes displays a single frame from the first couple of seconds.  If I hit pause, and then play again, or skip forward or back a little, it starts working.  

On the netbook, I get an early frame, frozen on the screen.  I hit pause, then play, then get moving video, but scrambled until a scene change or something which requires a complete image refresh, then it works.

I've tried using the different video output modules, but get the same issue with all of them.

Any thoughts?

I have exactly the same problem with VLC. It's black for about 4 seconds then the picture shows. It's software related, no other player does it to me and it's not my hardware.

---

### Post by musther on 2009-02-20
No, not my hardware either, and I've tried turning overlay off, no effect.  

I noticed that if I just wait, it works after a while too, maybe 3 or 4 seconds.

So, I was wondering if it was the title overlay, which displays the filename for 5 seconds, so turned that off, but it made no difference.

Any further thoughts?

---

### Post by zero777zero on 2009-02-20
this is inherent to way many video codecs are, it is codec dependent.

---

### Post by musther on 2009-02-21
Don't have any problem in totem, same videos play fine.  I'm getting this terminal output:

```
avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
```

No, computer is not too slow, and after the first five seconds, it plays perfectly - seems to be a VLC bug.

---

### Post by sonicb00m on 2009-02-21
It's just a problem with VLC. It's still not the final version, you'll have to compile it yourself if you want to try a newer build.

---

### Post by musther on 2009-02-21
Yes, have tried the 0.9.8a build, still the same issue.  I know it's a VLC problem, but I was hoping that we could identify the problem, then maybe it will be fixed for the final release.  I mean, I have this problem, and others do to, but clearly not everyone does.

---

### Post by sonicb00m on 2009-02-21
> **musther said:**
> Yes, have tried the 0.9.8a build, still the same issue.  I know it's a VLC problem, but I was hoping that we could identify the problem, then maybe it will be fixed for the final release.  I mean, I have this problem, and others do to, but clearly not everyone does.

I didn't have the problem on the previous version. It's not clear what what version people are reporting the error with. Im using 0.9.4

---

### Post by musther on 2009-02-21
My problem is on 0.9.4, but I have the same problem when trying 0.9.8a.  Somebody on the VLC forums said it was fixed in 1.0.0?

---


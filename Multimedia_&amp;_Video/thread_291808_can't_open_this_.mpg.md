---
title: "can't open this .mpg"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by songo on 2006-11-03
I can't see this video on [http://www.jahraw.com/media/video.mpg](http://www.jahraw.com/media/video.mpg)(this file has 40+ MB)
I apreciate if some one could download it and tell me which app (or lib) I should try.
I've tried with vlc and real player and nothing. real player says that he needs video/quicktime (?) and vlc says below.

thanks

```
main debug: using demux2 module "mp4"
mp4 warning: DEMUX_GET_FPS unimplemented !!
main debug: `/opt/vidz/video.mpg' successfully opened
main debug: EOF reached
main debug: closing input
mp4 debug: freeing all memory
main debug: removing module "mp4"
main debug: removing module "access_file"
main debug: thread 2985896864 joined (input/input.c:401)
main warning: refcount is 1, delaying before deletion (id=302,type=-7)
main: nothing to play

```

---

### Post by K.Mandla on 2006-11-03
I believe you probably want the w32codecs, and a suitable player. Try the [Restricted Formats page in the wiki]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5").

---

### Post by songo on 2006-11-03
nop. i've been there. but I can play other mpg files... why not this one?

---

### Post by yabbadabbadont on 2006-11-03
```
/home/bubba/temp $ tcprobe -i video.mpg 
[tcprobe] Apple QuickTime movie file
Segmentation fault

```
Apparently, it is a (broken) Apple QuickTime file...

By the way, you might want to add a warning to your first post that the file is 40+ megabytes.

---

### Post by songo on 2006-11-03
> **yabbadabbadont said:**
> ```
/home/bubba/temp $ tcprobe -i video.mpg 
[tcprobe] Apple QuickTime movie file
Segmentation fault

```
Apparently, it is a (broken) Apple QuickTime file...
Apparently... I tried with mplayer and I get
```
Playing /opt/vidz/video.mpg.
Quicktime/MOV file format detected.
No stream found.
```

So.. that means what? that I can't see this video at all?
> 
By the way, you might want to add a warning to your first post that the file is 40+ megabytes.
I'm sorry for that :oops: and thanks a lot.

---


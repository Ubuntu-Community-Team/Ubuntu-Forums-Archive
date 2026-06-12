---
title: "re-encoding downloaded videos to HD video"
date: 2013-03-30
forum: Multimedia Software
---

### Post by hurtstotalktoyou on 2013-03-30
Hi guys.

I have a bunch of random videos I downloaded from the internet, in various formats which are not too obscure.  They use stuff like DivX, XviD, and so on.  Unfortunately, some of them do not play back in my thumb drive player.

So I would like to re-encode them to something compatible.  Ideally I would like to encode them to something in HD, like 720p or 1080p or something.  Maybe H.264 is appropriate here.  My thumb drive player plays almost every HD video I download, so this is a good bet.

Command line tools are fine!  In fact, I prefer command line if possible.

Oh, and before anyone asks:  yes, I do realize that converting to HD does not improve video quality.  But some of my videos are already in HD, and so I want to preserve as much of the existing quality as possible.  Also, it will be convenient to have everything in the same format.

I would have expected questions like this have already been asked and answered on this forum, but for some reason I can't seem to find anything.  But maybe I just didn't look hard enough, so feel free to post a link if you think it applies here.

Thanks!

---

### Post by evilsoup on 2013-03-30
The 1080 in 1080p (and the 720 in 720p) refers to the height of the video. If your video is smaller, there is no advantage in upscaling it.

Use this command:

```

ffprobe input.file

```

...and run it over one file that works on your player, and one file which doesn't work, and paste what it says here. That will give a clue as to what the problem is. It's possible that you need to transcode to h.264, though that seems like a strange situation to me - most players that can handle h.264 can handle xvid/divx.

---

### Post by vanadium on 2013-03-30
You will first need to determine which container format and which codex your player does handle. Then indeed, you can batch-encode the whole stuff to this "common" format using avenc. There will be no need indeed to upscale video of lower resolution, which is a waste of disk space and processing time.

---

### Post by sudodus on 2013-03-30
I suggest that you learn ***ffmpeg***, which is a powerful command line tool. And consider the advice given already: You need not change the frame size from that in your existing video-ciips. It is enough to change the encoding (codec) and the container (evident by the file extension) to something that works in your thumb-drive player.

H.264 gives very efficient compression, but needs more horsepower than basic mpeg4 to play.

---

### Post by vanadium on 2013-03-31
About ffmpeg:
```

~$ ffmpeg
ffmpeg version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

```
so indeed it looks we need to head into avconv, although much of the documentation for ffmpeg will apply to avconv as well.

---

### Post by sudodus on 2013-03-31
> **vanadium said:**
> About ffmpeg:
```

~$ ffmpeg
ffmpeg version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

```
so indeed it looks we need to head into avconv, although much of the documentation for ffmpeg will apply to avconv as well.

There are several people who are still developing ffmpeg and several people at the Ubuntu Forums who support advanced use of it. Avconv is a fork competing with ffmpeg. I think both are feasible. If you need the bleeding edge features, you can get the source code and compile it from the developer, but I don't need that. The version than can be installed from the Ubuntu repositories is good enough for me.

---

### Post by vanadium on 2013-04-01
Thank you for this background info. In that case, it is not nice that such a message is included in the binary distributed with the Ubuntu software center.

---

### Post by FakeOutdoorsman on 2013-04-01
The previous message was even worse. I and others tried to get it changed to a more informative and less confusing/misleading message, but this was the result. I suppose I shouldn't be surprised since the "ffmpeg" package maintainer is a libav developer.

---


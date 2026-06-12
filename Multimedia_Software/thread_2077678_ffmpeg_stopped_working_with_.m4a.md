---
title: "ffmpeg stopped working with .m4a"
date: 2012-10-29
forum: Multimedia Software
---

### Post by bill-lancaster on 2012-10-29
This code (to extract a section) has worked well for a long time

ffmpeg -vcodec copy -ss 71 -t 624 /home/bill/Music/recordings/source.m4a /home/bill/Segment-01.m4a

But has now stopped working.

First I get "...source.m4a already exists - OK to delete"
Then with:-

ffmpeg -i aa.m4a -ss 00:00:00 -t 00:05:00  -acodec copy new.m4a

I get:-

ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
aa.m4a: Invalid data found when processing input

Any help would be appreciated.

Ubuntu 12.04
KDE SC Version 4.9.2

---

### Post by FakeOutdoorsman on 2012-10-29
> **bill-lancaster said:**
> This code (to extract a section) has worked well for a long time

```
ffmpeg -vcodec copy -ss 71 -t 624 /home/bill/Music/recordings/source.m4a /home/bill/Segment-01.m4a
```
You're applying your options to your input when you should be using them as output options, so move them past the input. The general syntax is:

```
ffmpeg [input options] -i input [output options] output
```

Which version of Ubuntu did it previously used to work in? 

> **bill-lancaster said:**
> ```
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
```


This means that you're not actually using the real ffmpeg. Unfortunately, as of 11.04, Ubuntu has switched from FFmpeg to a fork which I've found (via many other users) is quite buggy. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017) for more inro.

---

### Post by evilsoup on 2012-10-30
I've just tried your second command on an M4A file (using avconv/ffmpeg on 12.04), and I can't replicate your problem. Are you sure there isn't just a problem with those particular files?

---

### Post by FakeOutdoorsman on 2012-10-30
> **bill-lancaster said:**
> ```
ffmpeg -vcodec copy -ss 71 -t 624 /home/bill/Music/recordings/source.m4a /home/bill/Segment-01.m4a
```

First I get "...source.m4a already exists - OK to delete"


Yes, evilsoup is correct. Now I see the problem. You did not include the "-i", and therefore it assumes that source.m4a is the output. Since it already exists it asks if you want to overwrite or delete it (what it assumes as the input exactly I'm not sure) resulting in a file with no content (0 bytes).

---

### Post by bill-lancaster on 2012-11-18
Thank you for your sugestions - sorry, have been away for a while.

1) The file is fine, plays with mplayer etc.
2) Have tried puting "-i" at various points but without success.

ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers.

But now, (as per original post)

ffmpeg -i source.m4a -ss 00:00:00 -t 00:05:00 -acodec copy new.m4a

produces a perfectly good segement.

I'll mark this as SOLVED but don't really understand!

---


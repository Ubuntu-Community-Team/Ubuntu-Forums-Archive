---
title: "Merge DVD's"
date: 2010-06-20
forum: Multimedia Software
---

### Post by mherrin on 2010-06-20
Hi all, hoping for some pointers to solve the following :

I have several DVD's that are split across 2 discs or 2 sides etc. that I would like to join together to one seamless image so I can play them on my new Popcorn hour box.

I've searched all over and come up with nothing.

Any ideas?
TIA
Mike,

---

### Post by nothingspecial on 2010-06-20
Back up the video files first, then type ```
cat video1 video2 >merged_video
```

If that doesn`t work try avidemux.

---

### Post by mherrin on 2010-06-20
The files are not in avi, but standard DVD VOB etc. files.

I want to leave them that way, too.

Surely you cannot concatenate these files?

---

### Post by mherrin on 2010-06-23
Well, I have found a guide to merging DVD's, but it's only for Window$...

In case anyone is interested, here's the link:
[http://www.videohelp.com/guides](http://www.videohelp.com/guides)

---

### Post by lisati on 2010-06-23
I think DVD shrink (a Windows program) can keep the vob files intact, sort of, keeping chapters, subtitles and soundtracks intact, but at the expense of any existing menu structure on the disk(s). I don't know if the Ubuntu-friendly equivalents I know of (e.g. k9copy) can do so.

---

### Post by wkulecz on 2010-06-23
> The files are not in avi, but standard DVD VOB etc. files.

I want to leave them that way, too.

Surely you cannot concatenate these files?

I know it sounds too good to be true, but when you rip a DVD you get 1GB VOB files as part of the DVD spec.  To make a single mpeg all you have to do is:

cat rippername-00?.vob > moviename.mpg 

and you are done!  The resulting single mpg file will play in Xine, Totum, Mplayer, etc. and likely your Popcorn Hour box too.  I know they work fine in my Viewsonic VMP-70 media player set top box.

There is a technical issue about mpg transport stream vs. mpg program stream, but a well designed set top can handle the issue automatically -- My ~$80 VMP-70 does.

You may need to read the fine print about max file sizes on your set top -- if it uses Fat32 you can't go bigger than 4GB.  My VMP-70 can read NTFS or ext3 filesystems and I've used files as large as 8.7GB successfully with it.

Having all our DVDs on the set top has been great for my wife who hates fumbling with the DVD disks and is easily confused by the stupid self-indulgent menus that interfere with actually watching the movie.

---

### Post by mherrin on 2010-06-28
Thanks for the replies, looking in to 2mandvd at the moment & compiling own dvd without menus.

---


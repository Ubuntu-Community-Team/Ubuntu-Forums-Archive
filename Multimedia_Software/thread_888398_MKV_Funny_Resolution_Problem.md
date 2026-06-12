---
title: "MKV Funny Resolution Problem"
date: 2008-08-13
forum: Multimedia Software
---

### Post by jcr1 on 2008-08-13
Hi all. 

Still having issues converting MKV into anything. The problem seems to stem from the MKV itself to start with.

Basically, looking at the stream properties of the MKV using MKVInfo, I get this:

```

+ Video track
|   + Pixel width: 936
|   + Pixel height: 528
|   + Interlaced: 0
|   + Display width: 1280
|   + Display height: 528

```

As it is clear to see the actual resolution of the video is 936*528, but something is somehow telling it to play at a size (display dims) of 1280*528. 

When playing at 1280*528 the image is normal, i.e. not stretched. Therefore the original Pixel dims on their own are squashed. 

My problem is therefore, that whichever method I use to extract the video and put it into another container (say MP4 for XBOX360 use) the video is copied as 936*528, which when played back is squashed.

I believe I could simply re-encode the video to a new size (e.g. ffmpeg -s 1280x528) this works, but of course I am then loosing all the benefit of being able to just copy the H.264 video without re-encoding. 

Is there a way round this with any video software or am I going to have to accept that I need to re-encode?

I have been trying to keep it simple by just using ffmpeg.

Thanks in advance.

---

### Post by shirilover on 2008-08-13
Using the information from MP4Box documentation below:
```

-par trackID=PAR : sets pixel aspect ratio of given track. PAR can be "none" to remove PAR info, or of the form "N:D" where N is PAR numerator and D its denominator. Only supported for MPEG-4 Visual and MPEG-4 AVC/H264

```

You could try this when adding your video:
```

mp4box -add video.264 -par=160:117 -add audio.aac dest.mp4

```

---

### Post by jcr1 on 2008-08-13
Thanks for that. I haven't used MP4box before...is it hard to use? If i use mkvextract to extract raw video and audio can i just use mp4box to package it...or somethign along those lines?

Thanks a lot!

---

### Post by shirilover on 2008-08-14
mp4box is part of the gpac package, which allows you to create a compliant ISO MPEG-4 base media files.

However, the file may still not be playable if the level of the video track was encoded is greater than High@4.1

MediaInfo is a great tool to use to find information about codecs and settings for a number of different A/V containers.

---

### Post by jcr1 on 2008-08-14
Ah yes this is probably also an issue. If the video track is say 5.1, how do I reduce it to 4.1?

---

### Post by shirilover on 2008-08-14
I found a couple of methods to do this, but they are both windows executables.

h264info -> [http://sourceforge.net/project/showfiles.php?group_id=138139&package_id=225029](http://sourceforge.net/project/showfiles.php?group_id=138139&package_id=225029)

binreplace -> [http://forum.doom9.org/showthread.php?t=132386](http://forum.doom9.org/showthread.php?t=132386)

These may or may not work in wine.

---

### Post by jcr1 on 2008-08-15
Nice one...I shall check them out.

Thanks.

---


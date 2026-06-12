---
title: "Urgen help needed converting videos to Windows-friendly formats"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by lwr on 2007-01-05
I've been trying to get some videos off Google Video and YouTube, and I thought everything was succesful, but none of the files work in properly in Adobe Premiere Pro. For the things I could find on Google Video, I just downloaded the .avi file, which works fine on Linux, but Premiere won't import it. For things on YouTube, I downloaded the .flv file then used ffmpeg to do the following:
```
ffmpeg -i ishfwilf.flv -ab 56 -ar 22050 -b 500 -s 640x480 ishfwilf.mpg

```Premiere likes these files a bit more, but there is no sound when I try and play them. I've been trying to use Avidemux to change the file types, but I don't really know what I'm doing. Your help on this would be really appreciated. I'm willing to try almost anything.

---

### Post by kd7swh on 2007-01-05
You may try being more specific for FFmpeg something like this may work well:

```
ffmpeg -i ishfwilf.flv -f avi -vcodec xvid -b 500 -acodec mp3 -ar 48000 -ab 56 -s 640x480 ishfwilf.avi
```

Make sure that the codec that you use in ffmpeg is installed on the computer with  Premiere on it.
XviD should work pretty well, you may not even have to do any codec installation for it either.
I think Adobe Premiere likes video with higher audio sample rates. the >  -ar 22050 maybe too low. 

(I haven't used  Premiere for over a year so I am sorry if some of this is rusty.)

I don't think Avidemux supports flash (flv) if it does it is through ffmpeg anyway.

good luck, and remember compatibility is all in the codecs.

---

### Post by SadaraX on 2007-01-07
> **kd7swh said:**
> I don't think Avidemux supports flash (flv) if it does it is through ffmpeg anyway.

Avidemux does not support flash. The reason is that the author of Avidemux could not find a spec to use for FLV. I am not sure what that means, but here is the thread about it:

[http://www.avidemux.org/pun/viewtopic.php?id=2185](http://www.avidemux.org/pun/viewtopic.php?id=2185)

I have no idea how the format could be added, but I am sure the author would be interested if there was a valid method for using it. I should probably go ask him about it once Flash 9 comes out for Linux.

---


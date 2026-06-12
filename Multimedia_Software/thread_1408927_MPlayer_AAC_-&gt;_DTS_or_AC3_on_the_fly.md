---
title: "MPlayer AAC -&gt; DTS or AC3 on the fly"
date: 2010-02-17
forum: Multimedia Software
---

### Post by kiplingw on 2010-02-17
My receiver can decode Dolby Digital (AC3) as well as DTS streams. This is useful because they can contain more than 2 channels, whereas uncompressed PCM it can only understand max two channels.

Since it can't read AAC, and some films I have are (wasn't my choice) encoded in it, I'd like to be able to have mplayer transcode the audio to either AC3 or DTS on the fly. That way, I can still have digital surround sound instead of it being forcibly collapsed to two channels.

Apparently there is a way to do this, but you need to use the mplayer audio filter (-af) lavcac3enc.

The officially packaged mplayer has it disabled. I would like to enable it, but I am not sure where this is done. There is the ffmpeg source package, the mplayer source package, and then there are bits and pieces of ffmpeg source that ship with mplayer. Somewhere buried in a configure script or a file somewhere, there is a switch to enable it, but I don't know where it is.

Kip

---

### Post by phoenix81000 on 2010-02-17
Hey,

On the fly recoding is a bit of a hassle, you could check out this post which describes a couple of options. Hope you get it to work:

[URL="http://ubuntuforums.org/showthread.php?t=1408330"]
http://ubuntuforums.org/showthread.php?t=1408330[/URL]

---

### Post by kiplingw on 2010-02-17
Looks like that chap couldn't figure out how to get it to transcode on the fly, but that avidemux might represent the middle ground in re-encoding. Thanks.

Kip

---

### Post by DodgeV83 on 2010-10-24
> **kiplingw said:**
> My receiver can decode Dolby Digital (AC3) as well as DTS streams. This is useful because they can contain more than 2 channels, whereas uncompressed PCM it can only understand max two channels.

Since it can't read AAC, and some films I have are (wasn't my choice) encoded in it, I'd like to be able to have mplayer transcode the audio to either AC3 or DTS on the fly. That way, I can still have digital surround sound instead of it being forcibly collapsed to two channels.

Apparently there is a way to do this, but you need to use the mplayer audio filter (-af) lavcac3enc.

The officially packaged mplayer has it disabled. I would like to enable it, but I am not sure where this is done. There is the ffmpeg source package, the mplayer source package, and then there are bits and pieces of ffmpeg source that ship with mplayer. Somewhere buried in a configure script or a file somewhere, there is a switch to enable it, but I don't know where it is.

Kip

In-case anyone looking for a solution to this happens across this thread (as I did), here is the solution:

[http://ubuntuforums.org/showthread.php?p=10021089](http://ubuntuforums.org/showthread.php?p=10021089)

---


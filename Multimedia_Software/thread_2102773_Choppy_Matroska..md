---
title: "Choppy Matroska."
date: 2013-01-08
forum: Multimedia Software
---

### Post by zozza on 2013-01-08
Hi, 

I am having problems playing Matroska (mkv) files in any media player (e.g. VLC) using Ubuntu 10.04.

The playback is horribly choppy and the screen fragments a lot (see attachment).  Audio is fine. 

This only happens with .mkv files.  Others like .avi are fine.

I have done this but it does not help: [http://forum.videolan.org/viewtopic.php?f=2&t=42328](http://forum.videolan.org/viewtopic.php?f=2&t=42328)

Any ideas?

Thanks.

---

### Post by evilsoup on 2013-01-08
Are these high-definition (720p or 1080p) videos? If you're on an older or weaker computer (like a netbook), you may simply not have the horsepower to view them. In that case, you could either re-encode them to a less complicated format like xvid - though this will probably about double your filesize; or you could reduce the frame size down to standard definition (or both). Either of those would be quite a lengthy process if your computer can't handle HD playback (possibly even 'leave it on overnight'-long).

From the command-line, you could try using ffmpeg to do that (I'd recommend using the version from [this PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg), since the version in the 10.04 repos will be comically out of date by now). To re-encode the video to divx:

```

ffmpeg -i input.mkv -c:a copy -c:v mpeg4 -vtag divx -q:v 3 output.mkv

```

To resize it at the same time, use the [scale filter](http://ffmpeg.org/ffmpeg-filters.html#scale) - this will resize a video to have a height of 480 pixels, keeping the aspect ration the same:

```

ffmpeg -i input.mkv -c:a copy -c:v mpeg4 -vtag divx -q:v 3 -vf scale=h=480:w=-1 output.mkv

```

**IF** they're *not* HD videos, you could maybe try remuxing the videos; it's maybe possible that there's something wrong with the container. Again, with ffmpeg:

```

ffmpeg -i input.mkv -c copy output.mkv

```

or

```

ffmpeg -i input.mkv -c copy output.mp4

```

---

### Post by zozza on 2013-01-15
Thanks - that worked great although for some reason I could not use the 'scale'.

Not sure why because I checked on the ffmpeg page and your text looked correct.

---

### Post by papibe on 2013-01-15
Just an extra thought...

In 10.04,  VLC does not have any kind support for video hardware acceleration. If you have an relative modern Nvidia card, I would recommend using the combo proprietary driver + VDPAU + SMplayer to play HD videos.

Regards.

---

### Post by evilsoup on 2013-01-17
> **zozza said:**
> Thanks - that worked great although for some reason I could not use the 'scale'.

Not sure why because I checked on the ffmpeg page and your text looked correct.

Sorry, I sometimes forget that a lot of people use the version in the repositories (which is either hilariously out of date or horribly out of date, depending on which version of Ubuntu you're running). To get all the filters described in the documentation, install a more recent version from [this PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg), or get the very very latest version (plus a few non-redistributable goodies) by [compiling it yourself](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

---


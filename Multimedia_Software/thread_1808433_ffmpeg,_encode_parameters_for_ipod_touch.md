---
title: "ffmpeg, encode parameters for ipod touch?"
date: 2011-07-20
forum: Multimedia Software
---

### Post by takayuki on 2011-07-20
Hi,

What are the ffmpeg parameters to encode video for ipod touch?

I installed ffmpeg from source with the extra codecs via this tutorial here:
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Here's my ffmpeg -i output:
ffmpeg version N-31558-g47b71ee, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul 19 2011 10:13:46 with gcc 4.5.2
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  8. 0 / 53.  8. 0
  libavformat  53.  6. 0 / 53.  6. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 27. 0 /  2. 27. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0


I'd been using ffmpeg and winff to encode vids for my ipod touch in ubuntu 9.04, but when I upgraded to 11.04 I can't seem to get encoded vids to work on the touch.

After installing ffmpeg and winff, I noticed winff did not have the usual ipod touch presets.  I tried using the old presets, but they errored out.

I've been searching on these forums and the net for the right ffmpeg parameters to get vids working.

Even if I encode an mp4 that plays on my computer, when I move it to the touch, it won't play.

I'm using GoodReader to play vids on the touch.  I tried loading the encoded vids into iTunes, then moving them to the touch (via my xp box) but no love there either.  Yes, I could move the encoded vids to iTunes, then via the advanced menu, re-encode them for the ipod.  But the xp box is slow and I'd rather use linux to encode and be done with it.

Hope all that made sense.  Thanks for any ffmpeg ipod touch encoding love.

thanks,

takayuki

---

### Post by Jahid65 on 2011-07-20
you can use handbrake. I find it helpful while converting video for ipod/iphone.

```
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get updat[B]e
[/B]
```

**then install handbrake from software-center.**

---

### Post by takayuki on 2011-07-21
thanks, Jahid65, that did the job! :)

---


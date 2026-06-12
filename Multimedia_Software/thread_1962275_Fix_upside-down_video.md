---
title: "Fix upside-down video"
date: 2012-04-20
forum: Multimedia Software
---

### Post by Penguinnerd on 2012-04-20
Hello all,

I have a .mov video file that was filmed upside-down on a cell phone camera. (oops)

I'd like to flip it right-side up. How can I do this?

---

### Post by BicyclerBoy on 2012-04-20
You could try this:
ffmpeg -i video.mpg -vf "transpose=0, transpose=3" out.mpg

you need a version of ffmpeg with video-filters..0.9 or later

[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)

---

### Post by FakeOutdoorsman on 2012-04-22
Another filter option:
```
ffmpeg -i input -vf vflip,hflip output
```

---

### Post by Penguinnerd on 2012-04-23
Sorry it took me so long to reply. I've been busy.

Neither works for me.

```
ffmpeg: unrecognized option '-vf' 
```

I guess I have an older version of ffmpeg.

---

### Post by FakeOutdoorsman on 2012-04-24
You can compile ffmpeg or use the PPA BicyclerBoy mentioned (I'm unsure if the version from the PPA supports filters, but it probably does). Compile guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

The guide will remove any existing ffmpeg, such as the one from the Ubuntu repository, but if you want to keep the repository version you can modify the guide. Simply skip the command that removes ffmpeg and then skip the ffmpeg checkinstall command. The compiled ffmpeg binary is still available, but not installed. To use it just navigate to the ffmpeg source directory and execute it:
```
cd ~/ffmpeg
./ffmpeg -i input -vf vflip,hflip output
```

---

### Post by Penguinnerd on 2012-04-25
I just decided to boot into 12.04 to do this.

It worked somewhat, but the result is very grainy.

I need this for a presentation on Friday. If I don't get it to look good by then, I can just invert the display output. That worked last time.

---

### Post by FakeOutdoorsman on 2012-04-25
Older ffmpeg versions use a low bitrate by default. I'm unsure what the repository version does. If your output is .mpg or .mp4, then add the *-qscale* option. Try values from 2 to 5. A lower value is a higher quality. A value of 2 can probably be considered **visually** lossless.

Note that recent versions of ffmpeg from FFmpeg default to the libx264 encoder if it is available and if the output is .mp4. If that is the case, then use *-crf* instead of *-qscale* or just use the default since it's not bad. I don't use "ffmpeg"/avconv from libav (which is what Ubuntu now uses), so I can't comment on its behavior.

So, to summarize, just add *-qscale 2*.

---

### Post by BicyclerBoy on 2012-04-25
FYI
The severinsson ffmpeg ppa is the real ffmpeg & does supports video filters.


ffmpeg -f image2 -i pic1.jpg -vf "vflip ,hflip" -s 640x360 out.jpg

ffmpeg version 0.9.1-4:0.9.1-0ubuntu1~jon1~lucid1, Copyright (c) 2000-2012 the FFmpeg developers
  built on Jan  7 2012 15:05:25 with gcc 4.4.3

---

### Post by Penguinnerd on 2012-04-27
Thank you all. I had the presentation today. We ended up using a different video file (For other reasons).

---


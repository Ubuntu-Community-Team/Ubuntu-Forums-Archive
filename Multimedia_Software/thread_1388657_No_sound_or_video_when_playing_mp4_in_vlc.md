---
title: "No sound or video when playing mp4 in vlc"
date: 2010-01-23
forum: Multimedia Software
---

### Post by Rasheeke on 2010-01-23
As the title says, when trying to play songs purchased off of iTunes I don't want to be limited to having to watch them through Virtualbox.

Anybody know how to get vlc or mplayer to play .mp4 videos in Ubuntu 9.10?

I've got vlc 1.0 and trying to convert them using ffmpeg didn't work, I keep getting the following error.

swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context

Any help in this matter would be appreciated.

---

### Post by andrew.46 on 2010-01-23
Hi Rasheeke,

If these files are encumbered with DRM protection you may be in trouble. However if it is simply a case of your system being unable to playback aac sound your position is a little better :). Run through the steps relevant for Ubuntu 9.10 here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then interrogate one of the files as follows:

```
ffmpeg -i **[COLOR="Red"]problem_file.mp4[/COLOR]**
```

making the obvious substitution of your *own* filename for *problem_file.mp4*. If you could post the complete terminal output here there may be a few hints...

All the best,

Andrew

---


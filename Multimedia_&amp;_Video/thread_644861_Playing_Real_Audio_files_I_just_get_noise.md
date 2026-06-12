---
title: "Playing Real Audio files I just get noise"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by gbragante on 2007-12-19
I don't know what's happened but my Ubuntu 7.10 computer stopped playing Real Audio files.
Trying to reproduce such files I get only a continuous noise.
I have tried to reinstall all sort of things: alsa-base, ffmpeg, w32codecs, totem, gstreamer but with no result.
Removing the package gsteamer0.10-plugins-ugly and trying to play a .ra file I was prompted to download and install a proper codec. I did that but, again I got only a continuos noise.
Is there any explanation and/or solution for this issue?

Thanks
Gianni

---

### Post by brennydoogles on 2007-12-19
> **gbragante said:**
> I don't know what's happened but my Ubuntu 7.10 computer stopped playing Real Audio files.
Trying to reproduce such files I get only a continuous noise.
I have tried to reinstall all sort of things: alsa-base, ffmpeg, w32codecs, totem, gstreamer but with no result.
Removing the package gsteamer0.10-plugins-ugly and trying to play a .ra file I was prompted to download and install a proper codec. I did that but, again I got only a continuos noise.
Is there any explanation and/or solution for this issue?

Thanks
Gianni

Have you tried installing realplayer? In terminal, you can do this with the command```
sudo aptitude install realplayer
``` I hope that helps!

---

### Post by srmantis on 2007-12-19
The solutions is in this post:
[http://ubuntuforums.org/showthread.php?t=642046](http://ubuntuforums.org/showthread.php?t=642046)

Files rm and rmvb with mplayer.

---

### Post by gbragante on 2007-12-20
Thank you everybody for the suggestions.
However I am not searching for alternatives, I just want to fix what once was working.
Some days ago Totem was able to play rm files and SoundConverter converted them to MP3.
Now such stuff is no longer working and I am still wondering why.
I can't beleive that an OS can quit some of it's features without a reason and there is no way to understand and fix this.
Further suggestions will be greatly appreciated

Thanks
Gianni

---


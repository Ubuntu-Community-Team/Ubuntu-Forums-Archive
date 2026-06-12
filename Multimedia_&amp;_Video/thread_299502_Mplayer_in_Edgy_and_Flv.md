---
title: "Mplayer in Edgy and Flv"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by juantovarm on 2006-11-14
Hello!
Using dapper i could open flv movies in mplayer, now that i am using edgy i can only open it in vlc, mplayer says :

Fatal error
Error opening/initializing the selected video_out (-vo) device

I have ffmpeg installed, w32 codecs, and basically the same config as in 6.06

When i play the movies in vlc then all the other aps that have sound go silent and i have to reboot in order to ragin sound

any ideas?

Juan

---

### Post by taurus on 2006-11-14
Maybe you need to use x11 for your video output!

---

### Post by juantovarm on 2006-11-14
X11 did the trick! Thanks, now i have another annoyance: when the flv opens, i get this message: 

requested audio codec family
[ap3] (afm=mp3lib) not available
Enable it at compilation

But i do have the flv sound

any ideas?

Juan

---

### Post by taurus on 2006-11-14
I guess you can either ignore it or download the source and build it yourself with afm=mp3lib enable during the ./configure step then!  And as far as I know, you have to click that little window to close it but mplayer still works fine.

---

### Post by juantovarm on 2006-11-15
Being new to the world of linux and Ubuntu, i have to say that things here are not really so difficult...once you learn how to...could you show me how to enable it during the /.configure step?

Thanks

---

### Post by taurus on 2006-11-15
I am not in front of my Ubuntu right now since it's in the office and I am still at home but you can see all the settings that you can include in ./configure with

```
./configure --help
```

---

### Post by sizzam on 2006-11-23
> **juantovarm said:**
> 

requested audio codec family
[ap3] (afm=mp3lib) not available
Enable it at compilation



The solution for this problem is found in [this thread]("http://www.ubuntuforums.org/showthread.php?t=286977"):

> If you use GUI(gmplayer skin), go to Preferences, then click "codecs & demuxer". Select "FFmpeg....." for audio codec family. You may select ffmpeg for video codec family too!


Changing that setting fixed it for me.

---

### Post by rykel on 2006-11-27
> **sizzam said:**
> The solution for this problem is found in [this thread]("http://www.ubuntuforums.org/showthread.php?t=286977"):



Changing that setting fixed it for me.

I am facing the same audio issue... yes, ffmpeg audio works, but the voice is out of sync...

---


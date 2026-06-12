---
title: "Unable to fast forward audio file"
date: 2010-01-04
forum: Multimedia Software
---

### Post by JohnBris on 2010-01-04
Just did a fresh install of Karmic, got all necessary decoders installed for video and audio playback...I think.

Problem is I can't forward/search in audio files I am playing. I mean I can only Play, Pause, Stop or "Next-track" a music file. Video files are fine.

I've tried Exaile, Rythmbox and even Totem. It is like the audio files are "half read-only".

If I drag a horizontal scroller in the music player and let it go, it will only jump back to the position where it is actually playing.

Has anyone experienced, this? I am a missing something in gstreamer or something like it?

Thanks in advance for any suggestions!

---

### Post by ajgreeny on 2010-01-04
My only suggestion is to try vlc which also allows you to play files, audio and video at faster and slower speeds, as well as jump from place to place in the file.  I can not see why you can't jump at the moment, however;  that seems very odd.

---

### Post by JohnBris on 2010-01-04
thanks, but I just happened to uninstall vlc as I am unable to play video, I can't locate the error for that other than that it happened on my previous install after I tweaked some other things. I've just come to accept that.

but I doubt that trying a fourth media player will solve the problem with the audio files. besides, I really like to have a library type player like rythmbox or Exaile.

thanks anyway, hopefully someone else could shed some light on the issue. although like 20 searches on ubuntuforums and various google browsing have resulted in anythng similar!

---

### Post by kars2mars on 2010-03-26
See this post - [http://ubuntuforums.org/showthread.php?t=999788](http://ubuntuforums.org/showthread.php?t=999788)

Basically, you need to install the gstreamer-0.10-fluendo-mp3 package.
If that doesn't work, try the instructions at the end of the above link.

---

### Post by no2498 on 2010-03-26
smplayer can do this if you get it installed
it will play the mp3's and mp4's

---


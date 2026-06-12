---
title: "Burning MKVs to dvd with subtitles"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by zerosystem on 2007-02-06
I have this MKV file that I'd like to burn to dvd. I followed the instructions from here:

[http://ubuntuforums.org/showthread.php?t=319197&highlight=mkv](http://ubuntuforums.org/showthread.php?t=319197&highlight=mkv)

I used the command in the second post and converted it to AVI, but in the process I've lost the subtitles. They were embedded in the MKV. Is there a way (such as changing the command somewhat) so that mencoder will also include the subtitles?

---

### Post by yabbadabbadont on 2007-02-06
Try adding the "-slang" or "-sid" options.  Read the manpages and help to find the correct way to use them.  Note that that will overlay the selected subtitle directly onto the output video.  I haven't yet seen a method that preserves them as optional subtitles when converting a video for DVD output.  There probably is such a way, I just haven't run across it yet.  :)

---


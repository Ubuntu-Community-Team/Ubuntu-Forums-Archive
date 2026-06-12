---
title: "Matroska/MKV playback issues"
date: 2008-07-05
forum: Multimedia Software
---

### Post by Jerrac on 2008-07-05
First question, what is the relationship between Matroska and CoreAVC? For a while I thought they were the same thing, and that the lack of good CoreAVC codecs for Linux was the source of my problems. But I was just looking at the CoreAVC site, and found that Matroska has a completely separate site...

Now for my actual problems.

First is that subtitles in mkv files are not working correctly. If there is more that one line of subtitles for when multiple voices are speaking, only one line shows. So I miss some of what is being said. Also, sometimes that subtitles show up in a huge font that goes off the screen. I haven't been able to find any settings that seem to address these problems in VLC, or even Media Player Classic on Windows.

Finally, most of the time, mkv files end up skipping frames a lot. Like if there is a panning motion, it will pan jerkily. Is this because of my computer? Or the codec? Or something else?

My computer:
Sony Vaio FE880E/H
1.7 GHZ Core 2 Duo Processor
2 gigs of ram
Intel 945 graphics.
Ubuntu 8.04

I have the latest mediabuntu packages like the sticky comprehensive guide said.

---

### Post by shirilover on 2008-07-05
VLC is notoriously bad at rendering stylized subtitles. I recommend using an svn build of MPlayer. A very nice guide can be found -> [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

As for the frame skipping, if the file is high resolution(1280x720 and larger) and using H.264 video, you may have problems playing it without enabling framedropping and setting the loop filter to skip all frames.

As for CoreAVC and matroska, there is no relation between the two at all. CoreAVC is an H.264 video stream decoder, and matroska is an audio/video container.

---

### Post by Jerrac on 2008-07-05
Thanks for the tip about mplayer! It seems to be working. :D

---


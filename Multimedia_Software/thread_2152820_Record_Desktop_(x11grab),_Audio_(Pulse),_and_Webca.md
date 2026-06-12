---
title: "Record Desktop (x11grab), Audio (Pulse), and Webcam with FFmpeg or AVconv"
date: 2013-06-09
forum: Multimedia Software
---

### Post by clockworkpc on 2013-06-09
Hi everyone,

Here is a script that works for me.  I use avconv but as far as I can tell it is exactly the same as ffmpeg.  If either one works for you, great!

I actually tried recording three simultaneous streams about a year or two ago, and back then it didn't work.  Now it works, but I have no idea why.  As far as I can recall I did everything exactly the same.  And even if the audio and video are slightly off, the purpose of this script is to create a set of bin files to be edited in OpenShot or Kdenlive or whatever video editor you use.

Let me know if this works for you.

```
#!/bin/bash
#Filename:~/bin/desktop_screencast.sh
#Released under a GPLv3 Licence by Clockwork PC

# Author's Note:
# I have decided that the best way to go about this is to record three separate streams:
# Audio, x11grab (desktop), and webcam.
# In theory, there should be no problem syncing the audio with either video stream,
# but for some reason avconv (which is the same as ffmpeg but seems to be recommended)
# gives me some error message when I try to create a single command for audio and x11grab/webcam AND
# run it simultaneously with the corresponding third stream.
# I'm not a programmer, it's beyond my understanding.
# The one neat thing about this script is that it does a reliable job of:
# A) Getting the three streams
# B) Naming them
# C) Putting them in a folder where I can find them
# D) Keeping things organised
#
# If you can think of a better way to do this,
# Please let me know at clockworkpc@gmail.com

# Create a directory with today's date
mkdir ~/Videos/Desktop_Recording/bin_$(date +%F_%A_at_%H:%M:%S)/ &
#Audio, named by today's date
avconv -f alsa -ac 2 -i pulse ~/Videos/Desktop_Recording/bin_$(date +%F_%A_at_%H:%M:%S)/$(date +%F_%A_at_%H:%M:%S)_audio.mp3 &
#Webcam, named by today's date
avconv -f video4linux2 -r 25 -s 640x480 -i /dev/video0 ~/Videos/Desktop_Recording/bin_$(date +%F_%A_at_%H:%M:%S)/$(date +%F_%A_at_%H:%M:%S)_webcam.mkv &
#Desktop, named by today's date
avconv -f x11grab -r 30 -s 1366x768 -i :0.0 -c:v libx264 -threads 0 ~/Videos/Desktop_Recording/bin_$(date +%F_%A_at_%H:%M:%S)/$(date +%F_%A_at_%H:%M:%S)_desktop.mkv

# From here it'll be easy to use OpenShot or some non-linear video editor
```

---

### Post by FakeOutdoorsman on 2013-06-09
> **clockworkpc said:**
> ```

# but for some reason avconv (which is the same as ffmpeg but seems to be recommended)
# gives me some error message when I try to create a single command for audio and x11grab/webcam AND
```

There are two sources of a tool named ffmpeg: the original from FFmpeg, and a temporary one from the fork libav. Since Ubuntu uses the fork (the package maintainer is a libav guy), a message tells users that this libav ffmpeg is "deprecated". Unfortunately there is no context so most users assume that ffmpeg in general is no more, which is of course not true. Also see:

[list]
[*][Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017)
[*][The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)
[/list]

There are differences between the real ffmpeg and avconv; although a casual user may not notice. FFmpeg development is very active and merges most changes from libav but libav generally ignores FFmpeg and has a reputation of NIH syndrome (would rather re-invent the wheel instead of acknowledging any work from FFmpeg).

If a user wants to use recent, real ffmpeg there are two easy options:

[list]
[*][Get a static build (simply download, extract, and run)](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453)
[*][Compile FFmpeg with a step-by-step guide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)
[/list]

---


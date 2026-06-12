---
title: "Bash script for extracting sound from videos"
date: 2010-02-19
forum: Multimedia Software
---

### Post by d3v1150m471c on 2010-02-19
This is a bash script I wrote because I hate doing this manually. It takes any video, like a youtube video, extracts the music/sound from it in .mp3 format, then deletes the old video.
Have fun. Note, you will need mencoder to use it.

```

#!/bin/bash
#
# Converts video to .avi format
# then extracts the mp3 from the avi.
#
echo -n "Enter the name of the video INCLUDING the extension and path: "
    read vin
#
#
#
echo -n "Enter the name of the new video WITHOUT an extension behind the path: "
    read vout
#
#
#
mencoder "$vin" -ovc xvid -oac mp3lame -xvidencopts pass=1 -o "$vout".avi
#
#
#
mencoder -of rawaudio -ovc copy -oac mp3lame -o "$vout".mp3 "$vout".avi
rm "$vin"
  rm "$vout".avi
echo "Video has been replaced with .mp3 file."
sleep 7
clear
exit 0

```

---

### Post by SuperSonic4 on 2010-02-19
Looks nice, just a few questions.

1. How to I change it to convert to ogg
2. What bitrate does it extract at
3. How many channels does it extract to

Just curious because normally I'd use an ffmpeg script

---

### Post by d3v1150m471c on 2010-02-19
probably 192 kb/s. That seems to be standard with the .mp3's i've come across. I always use mp3 but if you want to convert it to ogg check out sound converter in the repos.

---


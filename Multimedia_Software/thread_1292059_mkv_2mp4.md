---
title: "mkv 2mp4"
date: 2009-10-15
forum: Multimedia Software
---

### Post by FunkyRes on 2009-10-15
Small shell script I wrote to take a h.264 + AC3 matroska .mkv file and transcode it to stereo mp4 that plays in totem with w/ fluendo codec pack installed.

It isn't terribly sophisticated, it assumes exactly 1 video track of h.264 and exactly one audio track of AC3 - but that's the only .mkv files I ever need to work with.

It does not re-encode the video, so you do not lose any video quality.

```

#!/bin/bash

base=`echo $1 |sed -e s?"\.mkv$"?""?`

vidTrack=`mkvinfo ${base}.mkv |grep "Track type" |grep -n "video" |cut -d":" -f1`
audTrack=`mkvinfo ${base}.mkv |grep "Track type" |grep -n "audio" |cut -d":" -f1`

mkvextract tracks ${base}.mkv ${vidTrack}:${base}.h264
mkvextract tracks ${base}.mkv ${audTrack}:${base}.ac3

a52dec -o wavdolby ${base}.ac3 > ${base}.wav
rm -f ${base}.ac3
normalize-audio ${base}.wav


ffmpeg -i ${base}.h264 -i ${base}.wav -map 0:0 -map 1:0 -vcodec copy -acodec libfaac -ab 128k -y -f mp4 ${base}.mp4

rm -f ${base}.h264 ${base}.wav

```

---


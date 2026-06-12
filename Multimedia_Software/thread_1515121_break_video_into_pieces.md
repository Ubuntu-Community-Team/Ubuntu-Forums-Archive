---
title: "break video into pieces"
date: 2010-06-21
forum: Multimedia Software
---

### Post by wesleybishop on 2010-06-21
is there a program that will break a video into ten minute pieces for youtube?

---

### Post by amauk on 2010-06-21
Most decent video editors allow you to specify start & end times (usually on a slider), so that when you export the video to a file, it only exports those bits
This is the GUI way, and you'll have to do it manually for every segment

but if you're looking for an automated way, I'd use FFmpeg

```
ffmpeg -vcodec copy -acodec copy -ss 0 -t 600 -i video.avi video-1.avi
```
is the basic syntax
-vcodec & -acodec are set to copy (so no transcoding takes place)
the -ss is the start time (in seconds)
and -t is the duration to copy
-i is the input file (your original video)
and the final arg is the output video

so, setting up a loop that extracts 10min segments, we have

```
#!/bin/bash

# example for a 30 min video (edit time to suit)
VID_TOTAL_LEN=1800

VID_SEGMENT_LEN=600

CUR_START=0
COUNTER=1
while [ "$CUR_START" -lt "$VID_TOTAL_LEN" ]; do
	ffmpeg -vcodec copy -acodec copy -ss $CUR_START -t $VID_SEGMENT_LEN -i video.avi video-$COUNTER.avi
	CUR_START=$(expr "$CUR_START" + "$VID_SEGMENT_LEN")
	COUNTER=$(expr "$COUNTER" + 1)
done
```

---

### Post by wesleybishop on 2010-06-22
Wow that looks complicated :) thanks for taking your time to do this for me. I am going to try this right now. How do I figure out the total video length?

---

### Post by XSAlliN on 2010-06-22
Avidemux can do that fairly easy.

---

### Post by wesleybishop on 2010-06-22
> **XSAlliN said:**
> Avidemux can do that fairly easy.

Would you mind telling me how? :confused:

Thanks :p

---

### Post by wesleybishop on 2010-06-22
tried this but could not seem to get it to work any other ideas

---

### Post by XSAlliN on 2010-06-22
Real easy:

Opened video with avidemux, set AUDIO from Copy to MP3 Lame (so the audio gets properly synchronised). Now split movie in to pieces by adding "A" (1'st selected frame) and "B"(last selected frame). You can find them down in main tools or  above with Edit (set marker A and set marker B).

So, you select 1'st frame of the video with "A" and move the slider till the end of the first piece of your pie, like 10 minutes (as you mentioned) and at 10 minutes you set B then save (file -> save -> save video or Ctrl+S). Then, from the ending of your first slice, you set "A" again and then move the slider till next 10 minutes, set B and save again, then keep on repeating the process. ):P

---

### Post by wesleybishop on 2010-06-28
Thanks to [XSAlliN]("http://ubuntuforums.org/member.php?u=248165") and [amauk]("http://ubuntuforums.org/member.php?u=384906") for there quick responses in resolving this problem :)

---


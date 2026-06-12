---
title: "Add an image to  the start of a video"
date: 2017-03-27
forum: Multimedia Software
---

### Post by bill-lancaster on 2017-03-27
I want a title image to show before a video clip starts.
Have seen many posts on this but this is the closest I can get
```
ffmpeg -i 028a.mp4 -i image1.png -filter_complex "[0:v][1:v] overlay=10:10:enable='between(t,0,5)'" output.mp4
```
This overlays the the png image rather than showing the image as an intro for say, 5 seconds.
Any advice would be welcome

Kubuntu 14.04

---

### Post by TheFu on 2017-03-27
I have a similar issue, but have no interest in using any overlay.  Also need a trailer to show all the tools used to create and edit the video, plus give credit for any audio and image files.  A 5 second per credit screen would be nice, if I can't get a scroll working - like they have in professional videos.

Option A
The best idea that I have is to display the image full screen, then use a screen recorder to capture it as a video for 5-20 seconds.  Then you can merge those together with the main video using normal editing tools. The important thing for simple editors is for the video rates and resolution and codec used to be the same.  OBS can merge the different inputs into a single output. [https://obsproject.com/](https://obsproject.com/)

Option B
Brainstorming here ... another method is to ask ffmpeg to take 1 image and repeat it at the same resolution/fps as the main video using the same vcodec.  I've seen this before, just haven't done it myself with all the new options that ffmpeg seems to have now.  I'll try to get that working. 

Would definitely be better than recording 20 seconds (option A), but might not be easier, short-term. There's a point where simple trumps elegant, right?

Plus I'm limited by which software I'm willing to install. I will not load anything based on Qt, so that removes the Kdenlive video editor from consideration. Personal issue.

---

### Post by bill-lancaster on 2017-03-27
Glad I'm not alone on this one!
I'm also looking for a command line solution.
I have the possibility of a) creating a video clip of the intro page and joining it to the main video but I'm having trouble matching the frame speed, resolution and codec.
and b) doing it in one step as described above.
I'll persevere and report any progress.

---

### Post by TheFu on 2017-03-27
I use this to get resolution and fps data about videos.
```
$ mplayer -identify -frames 0  file.mkv
```

Actually have a little script that does it and makes a table for multiple input files.  It isn't perfect - only 1 audio track is shown and no SRT or subs are listed.  Ran out of room inside my normal terminal width. ;(

For example:
```
Type      h:m:s   VCodec     WxH    Aspect VRate  ACodec  AChan Filename
-------- -------- ------  ---------  ----  -----  ------  ----- --------
lavfpref    44:11   h264  1280:720   0.00  59.94    ac3   2     Firefly-101-The_Train_Job.mkv
lavfpref    44:22   h264  1280:720   0.00  59.94    ac3   2     Firefly-102-Bushwacked.mkv
lavfpref    44:17   h264  1280:720   0.00  59.94    ac3   2     Firefly-103-Our_Mrs_Reynolds.mkv

```

Also use mkvinfo to grab data from mkv containers.

```
$ mkvi.sh Firefly-101-The_Train_Job.mkv 

===[ Firefly-101-The_Train_Job.mkv ]===

| + Duration: 2651.746s (00:44:11.746)
|  + Codec ID: V_MPEG4/ISO/AVC
|  + CodecPrivate, length 45 (h.264 profile: High @L3.2)
|  + Codec ID: A_AC3
|   + Channels: 6

```
That one is much simpler. Just highly selective egreps. The code:
```
$ more ~/bin/mkvi.sh 
#!/bin/bash

for filename in "$@"; do

   echo "

===[ $filename ]===
"
   mkvinfo  $filename | egrep 'Duration:|CodecPrivate|Language:|Codec ID:|Channels:' | egrep -v und

done
```

Anyway - lots of ways to get information about video files from a shell.

---

### Post by bill-lancaster on 2017-03-28
This works for me:-
```
~$ ffmpeg -f concat -safe 0 -i mylist.txt -c copy outputE.mp4
```
Where mylist.txt is:-
```
# this is a comment
file '/path/to/file1'
file '/path/to/file2'
file '/path/to/file3'

```

Found this at [https://trac.ffmpeg.org/wiki/Concatenate](https://trac.ffmpeg.org/wiki/Concatenate)

Thanks for the ideas

---

### Post by TheFu on 2017-03-28
```
mkvmerge -o output.mkv file1.avi + file2.mp4 + file3.mkv 
``` - each has to use the same codec, frame rates, tracks, but they do not need be in the same type of container. It is like a copy. No transcoding possible.

Normally, it would be 
```
mkvmerge -o output.mkv file1.mp4 + file2.mp4 + file3.mp4 
``` since all the files would be from the same creation.

If you don't use the '+', then you can add tracks, not concatenate.  Handy for adding captions or an audio track.
```
mkvmerge -o output.mkv file1.mp4  file1.ogg file1.srt 
```
That would probably result in 1 video track, 2 audio tracks and 1 caption track.

---

### Post by bill-lancaster on 2017-03-29
Huh!  Spoke too soon.
```
~$ ffmpeg -f concat -safe 0 -i mylist.txt -c copy outputE.mp4
```
Works but there is no audio in the output file.

The mkvmerge approach is interesting - I'm still messing with it.

---


---
title: "Convert all videos from HD to SD"
date: 2016-05-23
forum: Multimedia Software
---

### Post by mbnoimi on 2016-05-23
Hi,

I've 6TB of videos and I want to convert only HD (or above) videos to SD for reducing the free space of my hard disk.

How can I do that?

I'm thinking about writing a shell script for doing that so it suppose it should contains on a loop:
[list=1]
[*]Find all HD (or above) files (I DON'T HOW TO DO IT)
[*]Convert all found files to smaller size (480p or similar)
[*]Delete all found files
[/list]

NOTE: Usually I use this command for converting large videos to small ones
```
avconv -i video.mp4 -s hd480 video.mp4
```

---

### Post by vanadium on 2016-05-23
"find" allows you to find files, and optionally execute a command on it. For example, following command would find all videos in the folders under your Video folder in home create a small version of each mp4 it finds:

```

find ~/Video -n '*.mp4' -execdir avconv -i "{}" -s hd480 "{}"small.mp4 \;

```
This would create a file video.mp4small.mp4. With more fancy bash scripting, this could be a more elegant name.
Also with find, you could subsequently find all mp4 files without mp4small in their name, and delete these, and finally rename the mp4small.mp4 files.

Be very careful: you are at risk loosing all your video files if you make a tiny mistake. From your question, one could suspect that you do not have a backup.

---

### Post by mbnoimi on 2016-05-23
> **vanadium said:**
> 
```

find ~/Video -n '*.mp4' -execdir avconv -i "{}" -s hd480 "{}"small.mp4 \;

```


Thanks but this isn't what I'm looking for because it finds all *.mp4 files while I want only HD files (some files are HD while others are not)

---

### Post by FakeOutdoorsman on 2016-05-23
```
ffmpeg -i input -vf "scale='min(640,iw)':-2" -c:v libx264 -preset medium -crf 23 -c:a copy -movflags +faststart output.mp4
```

[list]
[*]Avoid avconv. It's junk. You can [download a binary of ffmpeg](http://johnvansickle.com/ffmpeg/).
[*]Using an [expression](https://ffmpeg.org/ffmpeg-utils.html#Expression-Evaluation) this will downscale anything above 640 pixels wide. It will automatically calculate the correct corresponding height to preserve the aspect ratio.
[*]Use the slowest preset you have patience for and highest -crf number that still provides an acceptable quality. Then use these same settings for the rest of your videos. See [FFmpeg Wiki: H.264](https://trac.ffmpeg.org/wiki/Encode/H.264).
[*]The audio will be [stream copied](https://ffmpeg.org/ffmpeg.html#Stream-copy) (re-muxed) instead of re-encoded.
[*]"-movflags +faststart" is for viewing via progressive download. Leaving it will do no harm.
[/list]

---

### Post by mbnoimi on 2016-05-25
> **FakeOutdoorsman said:**
> ```
ffmpeg -i input -vf "scale='min(640,iw)':-2" -c:v libx264 -preset medium -crf 23 -c:a copy -movflags +faststart output.mp4
```
Thanks FakeOutdoorsman for great advice. I'll definitely replace avconv with ffmpeg depending on your suggestion but your suggestion doesn't serve the main purpose of my thread,

I want to know how can I find HD (and above) video files (using find or any other tool)?

---

### Post by FakeOutdoorsman on 2016-05-25
You can use ffprobe to determine the width and/or height which can be used as a variable in a bash if/then statement.
```
$ ffprobe -v error -select_streams v:0 -show_entries stream=width -of default=noprint_wrappers=1:nokey=1 input.mp4
1280

```
Not a complete solution but should be useful.

---


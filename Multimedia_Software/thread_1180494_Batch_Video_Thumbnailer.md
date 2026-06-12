---
title: "Batch Video Thumbnailer"
date: 2009-06-06
forum: Multimedia Software
---

### Post by NEUR0M4NCER on 2009-06-06
I've searched and searched. The most promising ideas came from [this]("http://ubuntuforums.org/showthread.php?t=812720&highlight=video+thumbnail") thread, but I can't figure out how to get ffmpegthumbnailer to do a batch command, and videocut won't do a single thumb, only multiples (it crashes with a floating error[?] if I tell it to just do single thumbs).

Basically, all I want is to specify a folder of .avi files, and end up with a single jpeg for each, with the same file name, and no extra overlay (size, date, etc). Can I do this with ffmpegthumbnailer somehow?


[CENTER]*******************EDIT*********************

Solved, thanks to FakeOutdoorsman
See posts below for solution.
[/CENTER]

---

### Post by NEUR0M4NCER on 2009-06-08
... bump.

---

### Post by NEUR0M4NCER on 2009-06-13
It can't be *that* hard!

---

### Post by FakeOutdoorsman on 2009-06-14
You can do this with "find" and FFmpeg.  First the example FFmpeg command:
```
ffmpeg -ss 00:00:05:00 -vframes 1 -i frank_murkowski_memorial_apehouse.flv apehouse.jpg
```
The *-ss* option sets the offset in hours:minutes:seconds:frames and *-vframes* is the number of frames to process, so in this example FFmpeg will create one thumbnail that is 5 seconds from the beginning.

Combine this with find:
[Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937)

And you get something like this:
```
find $HOME -name '*.ogg' -type f -exec ffmpeg -ss 00:00:05:00 -vframes 1 -i '{}' '{}'.jpg \;
```

---

### Post by NEUR0M4NCER on 2009-06-16
Intriguing - thanks for that, FakeOutdoorsman. I'll give it a go tomorrow.

---

### Post by NEUR0M4NCER on 2009-06-16
It works like a charm! Thanks for that, I never would have thought to combine two commands. Should anyone else find this with the same needs:

I found it easier to navigate (cd) to the directory in question, and then omit the $HOME part. Also, I'm using the command to add screenshots to [TheTVDB]("http://www.thetvdb.com"), which require (for 4:3 shows) a 400x300px image size - this means adding '-s 400x300' before the output name brackets... this is the last one I used:
```

find -name '*.avi' -type f -exec ffmpeg -ss 00:06:05:00 -vframes 1 -i '{}' -s 400x300 '{}'.jpg \;

```

Thanks again, FakeOutdoorsman - this is something that will save me an awful lot of time and benefit many media centre users worldwide.

---


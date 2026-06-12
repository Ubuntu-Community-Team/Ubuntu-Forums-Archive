---
title: "how can I cut a part of video?"
date: 2016-01-12
forum: Multimedia Software
---

### Post by basma2 on 2016-01-12
Hello;

please I have openshot and I want to know how can I cut a part of this video its lenght is 1:54 I want to cut it to be 1:36 .I listened video in youtube but I can't do like it. I use the scissors tool and cut the wanted part but then I do not know what is the next step could any one help me please?

---

### Post by Bucky Ball on 2016-01-12
Perhaps it's a good idea to make a copy of your original video to practice on, if you haven't done that already. Once you've done that, experiment. You don't sound far away. If you make a wrong cut, hit control+z to undo.

Just mark out the section you want to cut with the razor tool and hit return? I've never used it but, as in [this thread which gives pictorial instructions]("http://ubuntuforums.org/showthread.php?t=2195201&p=12881037&viewfull=1#post12881037"), it can't be that hard. :)

You could also simply drag the beginning or the end of the clip to where you want and save that as a file.

---

### Post by shantiq on 2016-01-12
or maybe quicker >>

IN YOUR CASE:

1:54 I want to cut it to be 1:36 

try:

```
 avconv -i INPUTFILE.mkv -c copy -ss 00:00:00 -to 00:1:36  OUTPUTFILE.mkv
```

or if you have ffmpeg

```
 ffmpeg -i INPUTFILE.mkv -c copy -ss 00:00:00 -to 00:1:36  OUTPUTFILE.mkv
```


General Info on Trimming Video
==================


```
avconv  -i INPUTFILE.mkv -c copy -ss 00:14:48 -t 00:01:18  OUTPUTFILE.mkv
```
```
 ffmpeg  -i INPUTFILE.mkv -c copy -ss 00:14:48 -t 00:01:18  OUTPUTFILE.mkv
```

where the first time is start time and second duration of cut piece 1:18

also ffmpeg allows you to do this

```
 ffmpeg -i INPUTFILE.mkv -c copy -ss 00:14:48 -to 00:16:06  OUTPUTFILE.mkv
```

with -to where second time is finishing time::: in this case you also end up with a 1:18 cut

```

-t duration         record or transcode "duration" seconds of audio/video
-to time_stop       record or transcode stop time
```
[FONT=comic sans ms][COLOR=#800000]-to NOT available in avconv[/COLOR][/FONT]

---


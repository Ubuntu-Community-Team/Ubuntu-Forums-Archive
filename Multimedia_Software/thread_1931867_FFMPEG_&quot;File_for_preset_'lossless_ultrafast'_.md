---
title: "FFMPEG &quot;File for preset 'lossless_ultrafast' not found&quot;"
date: 2012-02-26
forum: Multimedia Software
---

### Post by splosh5 on 2012-02-26
Hello, when i try to run the following script to record my desktop, I get this error message "File for preset 'lossless_ultrafast' not found".

```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y output.mkv
```I followed fakeoutdoorsman's tutorial to install FFMPEG.

How could this be solved?

Thanks,
Josh.

---

### Post by ron999 on 2012-02-26
> **splosh5 said:**
> ...I get this error message "File for preset 'lossless_ultrafast' not found".

Hi
The presets have changed.
Preset "lossless_ultrafast" doesn't exist any more.

When you use command "**x264 --help**" it shows available presets:-
> --preset <string>       Use a preset to select encoding settings [medium]
                                  Overridden by user settings.
                                  - ultrafast,superfast,veryfast,faster,fast
                                  - medium,slow,slower,veryslow,placebo

So modify part of your FFmpeg command...
from this:-
```
...-vcodec libx264 -vpre lossless_ultrafast -threads 0...
```
to this:-
```
...-vcodec libx264 -preset ultrafast -crf 0...
```

---

### Post by splosh5 on 2012-02-26
Thank you ever so much, that has worked perfectly! I did a post where i am getting a error when installing programs though the Ubuntu software center, not sure you would know how to fix it? [http://ubuntuforums.org/showthread.php?p=11720087#post11720087](http://ubuntuforums.org/showthread.php?p=11720087#post11720087)

Really many thanks,
Josh.

---

### Post by ron999 on 2012-02-26
Hi
I edited my post, added "-crf 0" to the command.
Did you use "-crf 0"?

---

### Post by splosh5 on 2012-02-26
No I dont think i did.

```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -y output.mkv
```

Many Thanks,
Josh.

---

### Post by ron999 on 2012-02-26
> **splosh5 said:**
> No I dont think i did.

This one:-
```
ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 30 -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -y output.mkv
```

;)

---


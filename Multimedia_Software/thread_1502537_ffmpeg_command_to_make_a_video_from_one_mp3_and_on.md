---
title: "ffmpeg command to make a video from one mp3 and one png"
date: 2010-06-05
forum: Multimedia Software
---

### Post by bcqdan on 2010-06-05
is there a command to create a video from a mp3 and a png suitable to upload on youtube if anybody knows?

---

### Post by ron999 on 2010-06-05
Hi

This is one way to do it.
If you have a png file with name **picture.png**.
And a mp3 file with name **soundtrack.mp3**.

First make a silent video with the correct length of time.
So if your mp3 track lasts for 198 seconds the command is:-
```
ffmpeg -loop_input -i picture.png -t 198 silent.mp4
```

Then add the soundtrack:-

```
ffmpeg -i silent.mp4 -i soundtrack.mp3 -vcodec copy -acodec copy movie.mp4
```

This gives you a mp4 file named **movie.mp4** suitable for YouTube.

---

### Post by bcqdan on 2010-06-06
that's great, thank you

finally a lossless conversion

---

by the way this is what i used and it worked really well:

```
 ffmpeg -i image.jpg -loop_input -t 206 -vcodec mpeg2video silent.mp4 
```

use mpeg2video codec instead of default mpeg4, better supported by youtube according to [http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=132460](http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=132460)

```
 ffmpeg -i silent.mp4 -i input.mp3 -acodec copy -vcodec copy -acodec copy -vcodec copy output.mp4 
```
copy both sound and video strems

---

### Post by FakeOutdoorsman on 2010-06-07
Here's a similar thread: [Convert mp3 to avi](http://ubuntuforums.org/showthread.php?t=1244112).  I give a FFmpeg example showing how to do everything in one step.

---

### Post by ron999 on 2010-06-07
@FakeOutdoorsman
That **-shortest** option is useful. We learn something new every day.:biggrin:

So the new improved version is:-
```
ffmpeg -loop_input -i picture.png -i soundtrack.mp3 -shortest -acodec copy movie.mp4
```

:guitar:

---


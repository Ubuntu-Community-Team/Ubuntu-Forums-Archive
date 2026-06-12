---
title: "Convert .mov to youtube?"
date: 2007-05-31
forum: Multimedia Production
---

### Post by tdrusk on 2007-05-31
I need a way to convert .mov to a youtube acceptable format (mpeg4 maybe?). I have tried using Avidemux, but it doesn't give me a good video, just a skippy one. Can someone maybe link me to a guide or something?

---

### Post by steeleyuk on 2007-06-01
Try using [www.media-convert.com](www.media-convert.com). Converts all sorts of formats and its fairly quick as well.

---

### Post by tdrusk on 2007-06-01
This says it will take 1 hour and 45 minutes. Any program ideas?

---

### Post by heathenx on 2007-06-02
install mencoder if you don't already have it.

issue this command in a terminal:

mencoder -ovc copy -oac pcm -o output.avi input.mov

---

### Post by tdrusk on 2007-06-02
> **heathenx said:**
> install mencoder if you don't already have it.

issue this command in a terminal:

mencoder -ovc copy -oac pcm -o output.avi input.mov

Thank you. It worked well after I ran this
```
~/Desktop$ mencoder -ovc lavc -oac pcm -o output.avi /home/tyler/Desktop/IMGP0262.MOV 

```

---

### Post by tdrusk on 2007-06-06
I am trying to figure out how to change the aspect ratio of a video I have. Right now, to convert my video, I am using this command.
Code:

mencoder -ovc xvid -oac mp3lame -xvidencopts bitrate=687 -o <output.avi> <input.avi>

What can I add to that to change my ratio to 4:3?
__________________

---


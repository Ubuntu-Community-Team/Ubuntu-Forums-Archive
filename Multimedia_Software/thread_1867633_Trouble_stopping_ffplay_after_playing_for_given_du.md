---
title: "Trouble stopping ffplay after playing for given duration."
date: 2011-10-23
forum: Multimedia Software
---

### Post by vamc on 2011-10-23
Hello. I want to stop ffplay after playing for given duration. From ```
ffplay --help
```, I came to know that -t option will do the trick. So, I tried ```
ffplay -t 30 <path/to/file>
```. The video did not stop after 30 seconds. The frame rate dropped and the video continued. I am using FFplay 0.6-4:0.6-2ubuntu6.1 in Maverick. 

Is there a way to stop the video?

Thanks in advance.

---

### Post by andrew.46 on 2011-10-25
I can confirm this in the latest git FFmpeg / FFplay so perhaps a bug? In the short term perhaps use MPlayer which works perfectly with something like:

```
mplayer -endpos 30 input_file
```

---

### Post by FakeOutdoorsman on 2011-10-25
Worked for me using Maverick's FFplay and playing [IronMan.mkv](http://mirror05.x264.nl/Dark/x264clips/IronMan.mkv) although it got blocky in the last second:
```
ffplay -t 5 -autoexit vbox/IronMan.mkv
```
What type of file is your input?

---

### Post by andrew.46 on 2011-10-25
Oooops..... was not aware of the *-autoexit* option.......

---


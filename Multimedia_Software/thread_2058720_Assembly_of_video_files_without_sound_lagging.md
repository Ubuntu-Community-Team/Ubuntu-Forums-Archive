---
title: "Assembly of video files without sound lagging ?"
date: 2012-09-16
forum: Multimedia Software
---

### Post by Odense on 2012-09-16
I am using Ubuntu 11.4 on my Samsung laptop.

I am sometimes using my cheap Blue Tinnum harddisk recorder to record movies from the cable TV. It
works well and they can be played back nicely with the Blue Tinnum recorder.

I would however like to be able to play them back on anything (as well as store them in a format with a better name and in a single fil.

The video is stored in 2 GB files with names like data0001.ts and data0002.ts and so on. I don't know what the true format is - but these files play with no problems in VLC.

I am going to convert the files to .mkv format with Handbrake but first I want to assemble them into one file - this I do with the following command in a terminal window:

cat data0001.ts data0002.ts > video.ts

Unfortunately in the new file (video.ts) the sound is lagging a little after the video - how do I avoid this ?

---

### Post by marinara on 2012-09-16
at the command prompt, type: 
man cat

---


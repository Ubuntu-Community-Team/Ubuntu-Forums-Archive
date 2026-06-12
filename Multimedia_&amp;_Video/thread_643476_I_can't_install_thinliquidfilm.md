---
title: "I can't install thinliquidfilm"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by RubberBinder on 2007-12-17
I am trying to convert some AVI videos into iPod friendly mp4 videos, but nothing works.
Winff just makes an empty file with an mp4 ending and thin liquidfilm wont install, it gives me an error in the install that says,

(File "./install.py", line 128, in <module>
os.symlink('/usr/local/thinliquidfilm/thinliquidfi lm.py','/usr/local/bin/thinliquidfilm')
OSError: [Errno 2] No such file or directory)

---

### Post by yabbies on 2007-12-17
DeVeDe can transcode to mpeg 4

---

### Post by RubberBinder on 2007-12-17
Devede doesn't allow for the resolution to be compressed into an iPod compatible size

---

### Post by yabbies on 2007-12-17
have a look at [convertIT]("http://ubuntuforums.org/showthread.php?t=567016")

---

### Post by philc on 2007-12-18
If you're OK with a command line, I've just written a bash script that converts input video to various H.264/MPEG-4 formats:

[http://ubuntuforums.org/showthread.php?t=643334](http://ubuntuforums.org/showthread.php?t=643334)

You'll need FFMPEG built with relevant x264 and xvid options.

---

### Post by RubberBinder on 2007-12-18
First off I am not a real big fan of the command line so I tried convertIT and it says it is doing something, but it just finishes without making any files. I am positive my AVI files work though so, I guess I'm doing something wrong. :confused:

---

### Post by Creative2 on 2007-12-20
....i must rewrite documentation and function....-.-''


ffmpeg -i INPUT -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192k -s 320x240 -aspect 4:3 OUTPUT

try this in terminal

if works for your ipod let me know because i have not ipod so i cant test......

cheers Creative2

---


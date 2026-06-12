---
title: "youtube avi to mov conversion"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by evaristegalois on 2007-07-26
I want to convert an avi (or mpeg) file to mov, preferably on the command line so that I can do batches of files and not just one file at a time. Reason: I want to watch youtube clips on my IPOD. The IPOD can pretty much only read *.mov files, certainly not *.avi or *.mpeg. 

I know how to convert the youtube *.flv files to *.avi (ffmpeg does a good job at that -- in order to get the *.flv files I use firefox, greasemonkey and Josh Kinberg's greasemonkey script, just in case you are interested).

But then I am stuck. I did a lot of searching on google but no luck with avi to mov. There is something for Windows called SUPER(c) which looks a bit suspect but it's not for linux anyways. Mencoder can only output to avi or mpeg. What to do?

---

### Post by Steveway on 2007-07-26
Mencoder can do a lot more than you say.
Read the manpage of Mencoder to get the info for the commands to use.
You can for sure convert those Videos to .mov with mencoder.
Here are just some of the supported fileformats:
MPEG/VOB, AVI, ASF/WMA/WMV, RM, QT/MOV/MP4, Ogg/OGM, MKV, VIVO, FLI, NuppelVideo, yuv4mpeg, FILM and RoQ

EDIT: And this Super is just a frontend to mencoder and ffmpeg.

---

### Post by Commodore Guff on 2007-07-26
Isn't ffmpeg able to convert to .mov?

---

### Post by evaristegalois on 2007-07-27
I installed mplayer and mencoder, and it can read *.mov files but not encode into them. Thus, it's easy to go from *.mov to *.avi but not the other way around. With the command

mencoder -of help

I get all the output formats that are supported and *.mov is certainly not one of them. With

mencoder myfile.avi -ovc lavc -oac pcm -o myfile.mov

mencoder just writes the file myfile.mov but it's encoded as an *.avi file. How do I need to tweak mplayer/mencoder to be able to encode into *.mov? I am also surprised that there aren't a lot of people who need this because if you want to see anything but home videos on your IPOD that's what you need to do.

---

### Post by evaristegalois on 2007-07-27
Oh yes, and ffmpeg has the same limitation. Great when you want to convert anything into *.avi, but no capability of converting into *.mov. Still, if anyone knows a command or a codec that needs to be installed to do this please let me know. I have ffmpeg and mencoder in working order on my computer.

---

### Post by evaristegalois on 2007-07-30
I had some more luck finding information by googling "conversion ipod video files" instead of googling "avi to mov conversion". Two really helpful sites are

[https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)
[http://www.pcworld.com/article/id,130546-page,1-c,mp3players/article.html](http://www.pcworld.com/article/id,130546-page,1-c,mp3players/article.html)

and, yes, this is more complicated than just using mencoder. You can read why this is the case on [https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding).

---

### Post by hod139 on 2007-07-31
```
ffmpeg -i in.avi -sameq out.mov
```

---


---
title: "adding subtitles to .avi (avidemux) help."
date: 2010-01-20
forum: Multimedia Software
---

### Post by JohnCDI on 2010-01-20
Well I know this is going to sound like a strange problem. I have a video file which I just recently added subtitles to permanently with avidemux. Now for some reason this newly created file with the subtitles i can only work with graphically. I've tried numerous times to just move the file in terminal in which i get a directory or file does not exist. My spelling is correct the file is only three letters long. Also in terminal it doesn't show the file as a video file and just shows it as regular text which all my other video files show up as a color or rather just beint executable. I can watch the movie but i'm trying to move the file to another server and stream it i've moved the file graphically but it wont stream due to it apparently not existing any help is appreciated.

---

### Post by lovinglinux on 2010-01-20
I guess the problem is that subtitle hard encoding in avidemux is actually some sort of hack and probably not supported by some hardware/software.

I would advice to use mkv container and embed the subtitles as separate streams, using mkvtoolnix. Unfortunately, I guess this method is not suited for online streaming. In this case I would advice to embed the subtitles with mencoder.

Here is an example of command:

```

mencoder source_video.avi -sub source_subtitles.ssa -*** -***-color FFFF0000 &#8722;***&#8722;font&#8722;scale 3 -o output_video.avi -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=1500
```


The *** in the code are "a s s" without spaces. The forum platform things I'm cursing, when in fact is a file format.

BTW, the moderators were pretty fast on removing the spammer I just reported. Nice job=D>

---


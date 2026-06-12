---
title: "Exporting With Kino"
date: 2007-06-06
forum: Multimedia Production
---

### Post by tdrusk on 2007-06-06
I pretty much want to use Kino for conversion. So I import a video (ogg theora) format and go to export. Any setting under the MPEG or Other tab does not work. Please help me, I really want to get a  decent video online.

Thanks!

---

### Post by finite9 on 2007-06-07
kino uses export scripts which use mencoder or ffmpeg to convert the video  I would suggest you use these tools directly for better results.  Look at the Mencoder website for examples on encoding video, as it is very extensive.

I too see the same problem, but I thought it worked OK in 0.8 which is in feisty, but I compiled 1.0 myself and then MPEG tab became greyed out for some reason.

You can find the export scripts in the main kino directory if you wan to see what they do.

---

### Post by tdrusk on 2007-06-07
Is there any program I can use to make the mencoder process easier. I really just need a frontend. Either that or can you tell me what I need to put in to be able to change the bitrate, frames per second, and aspect ratio?

EDIT: I found Pitivi. It's pretty sweet and does the job as far as I can tell. I need to mess with the settings a little bit more to get decent quality though.

---

### Post by finite9 on 2007-06-07
sorry dude...im not a elitist geek, but the term "read the manual" really does apply in the case of mencoder.  Ive spent countless hours reading man pages and web sites to get where I am, and one thing ive realised is that your needs are probably completely different from my needs.  Try -fps and -ofps (output fps) in mencoder and -aspect 16:9 or -vf scale for aspect.  It probably doesnt help to just state the command--you probably need to read up on how the switch is used.  Bitrate im not sure of.  Here is my command to convert dv files to Quicktime7 compatible H.264, but it is probably not at all what you need:

```
## following will create Quicktime7 compatible MP4 file, but is not
## best quality possible with x264
mencoder $infile -o /dev/null \
-ovc x264 -vf harddup,kerndeint,hqdn3d,scale=-10:-1 -of rawvideo \
-x264encopts subq=6:partitions=all:me=umh:frameref=5:threads=auto:pass=1:turbo=1 \
-nosound
## second pass
mencoder $infile -o /tmp/"$infile2"h264 \
-ovc x264 -vf harddup,kerndeint,hqdn3d,scale=-10:-1 -of rawvideo \
-x264encopts subq=6:partitions=all:me=umh:frameref=5:threads=auto:pass=2 \
-nosound
```

---


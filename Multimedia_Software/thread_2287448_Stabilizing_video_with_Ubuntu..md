---
title: "Stabilizing video with Ubuntu."
date: 2015-07-19
forum: Multimedia Software
---

### Post by Roasted on 2015-07-19
Hello friends. I have made some headway in my search for stabilizing video in Ubuntu, but I'm curious about refining the process a bit. Long story short, I do some work with a recumbent bike shop which focuses a large portion of their energy towards adaptive cycling for those with physical limitations. The folks in question are often asked if they are interested in having pictures/video taken of them in an effort to share with the wider community to act as an inspiration to others. I'm trying to do these videos justice in the best way possible. Given some of these videos are taken while walking/cycling next to these folks, they're often a little shaky. 

I found "transcode" in the repos, a command line way to stabilize videos. And you know something, it works *great*. In particular, I was [following this post]("https://isenmann.wordpress.com/2011/03/22/deshaking-videos-with-linux/") to get started. Realistically I was only using two commands.

```
transcode -J stabilize -i INPUTVIDEO.MOV
```
```
transcode -J transform -i INPUTVIDEO.MO -y raw -o OUTPUTVIDEO.MOV
```

Here's one area where I get hung up. In my mind, I favor the idea of doing a raw dump, which my understanding is it's lossless. The particular videos I'm working with came as .MOV on my camera. Transcode dumps an edited .MOV into the same directory, but with a massive file size difference. The original being 23 MB, where the new one is 788 MB. It scales up from there (350 MB videos balloon to 10.0 GB, etc). I then load them into Handbrake to get more manageable files to work with, resulting in a nearly identical file size as the original source when done (23 MB original, 26 MB when handbraked with video quality set to 16).

I'm curious if I could cut out the center piece where I have these large files on my drive in between. I have enough storage to manage it (on my desktop), but in the name of making things more efficient and straight forward, perhaps I can utilize transcode to do it on the fly. I see on the web site transcode can pipe to (in the example) xvid4, but I understand xvid4 is kind of legacy at this point. I saw no mention of avconv in the man page (though it supports ffmpeg - maybe ffmpeg parameters will help?). Given I'm on a 14.04 machine, avconv is what's here by default.

Do you folks have any ideas of what I could do to transcode these files into a, do I dare say, more "mainstream" container/render in one shot without having the larger raw files hanging out on my drive in between the process? While my desktop with oodles of HDD space can manage this, I wonder about doing it on my 128 GB SSD laptop where 22 minutes of video transcoded raw dumps to 55 GB total. I don't know enough about all of the underpinnings of video encoding/etc to know offhand what makes the most sense for this project. Realistically, I can (and maybe will) just run with raw transcodes + handbrake since it gives me an *awesome* result, but as I said, if I can simplify things, I'm all for it.

Any ideas, folks? Thanks ahead of time!

---

### Post by blm-ubunet on 2015-07-20
You can "pipe" the files through a filter scaler etc to an output file.
ffmpeg (using deshake filter) supports pipes in & out.

I didn't pipe the whole process because I was repeatedly tweaking settings ..
Should be clues in the following:

f```
fmpeg -i your-input-video.mov -vf "crop=720-40:576-30:0:0, scale=720:576, deshake=-1:-1:-1:-1:16:16:2" -f yuv4mpegpipe -y stream.y4m
ffplay -i stream.y4m 
```
(could pipe the above ffmpeg | ffplay -i -)
I was repeatedly using above raw video so did not pipe into yuvfps..
```
cat stream.y4m | yuvfps -w -r 50:1 -s 17:1 | ffmpeg -f yuv4mpegpipe -i - -vcodec mpeg2video -flags +ilme+ildct -target pal-dvd  -b 8000k -y new2.mpg
```
PAL DVD mpeg2 interlaced shows combing if encoded from yuvfps -r 25:1 etc..

I was using "mjpegtools" on quicktime dv mov to change frame rate because this is an area where ffmpeg is very weak. You don't need that.
HTH.

---


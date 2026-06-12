---
title: "How do I create a video DVD from Pitivi output?"
date: 2010-11-17
forum: Multimedia Software
---

### Post by skywatcher on 2010-11-17
I want to burn a video DVD that will play on a standard DVD player. How do I convert the ogg theora (or other) output format obtained after rendering with Pitivi, to the two folders that need to be burned onto the DVD, i.e.,  VIDEO_TS AND AUDIO_TS?

---

### Post by ghostborg on 2010-11-17
You need a Video DVD Creator program.

Type in DVD in the search of the Ubuntu Software Center.

A couple are:
Bombono
ManDVD - Getdeb.net has 2ManDVD 1.4.4-1~getdeb1 the successor to ManDVD.

A couple of other usefull tools are
Handbrake- encoder
Devede- program to take a video file and create a simple dvd with a menu.

Openshot Video editor looks good too.

---

### Post by skywatcher on 2010-11-17
Thanks, I'll give them a try.

---

### Post by skywatcher on 2010-11-17
Is there no way that I can simply convert ogg theora to the correct format for a video DVD? I tried ManDVD, but it overflows the screen and I can't see the buttons at the bottom. I also tried Devede, but I get an error that says "... it seems to be a bug of Mencoder". Besides, both these programs, when I install them from the Ubuntu Software Center, require that I remove certain lib installations. Why?

Alternatively, is there a video editor for Linux that will do what Nero does on Windows? I used Nero some years ago and I was able to burn a video DVD directly from the program.

Pitivi seems great - I got the hang of it in half an hour. But it is of no use at all if I can't copy my video creation onto DVD.

---

### Post by ron999 on 2010-11-17
Hi skywatcher

I previously used **tovid** to make a DVD from a file.

But now I use this method instead, just 3 steps.

#1 Convert the file to mpeg2.

```
ffmpeg -i < filename > -target pal-dvd foo.mpg
```
or
```
ffmpeg -i < filename > -target ntsc-dvd foo.mpg	
```

#2 Create a title.
(Folder named DVD containing VIDEO_TS and AUDIO_TS folders with VTS_01_0.IFO and VTS_01_0.BUP etc. files)

```
dvdauthor -o DVD/ -t foo.mpg
```

#3 Create a table of contents. (VIDEO_TS.IFO and VIDEO_TS.BUP files)
```
dvdauthor -o DVD/ -T
```

---

### Post by skywatcher on 2010-11-18
Hi ron999

Thanks for the help - it works like a dream!

---

### Post by VanillaMozilla on 2011-03-24
> **skywatcher said:**
> I want to burn a video DVD that will play on a standard DVD player. How do I convert the ogg theora (or other) output format obtained after rendering with Pitivi, to the two folders that need to be burned onto the DVD, i.e.,  VIDEO_TS AND AUDIO_TS?
Watch out!  You do not want Ogg Theora.  You want FFmpeg MPEG-2 PS format (DVD VOB) muxer [ffmux_dvd].  For sound use FFmpeg ATSC A/52A (AC-3) encoder [ffenc_ac3].  Video is FFmpeg MPEG-2 video encoder [ffenc_mpeg2video] but you will definitely want to reset the bitrate from 300000 to something much larger.  I found 6548000 on the Interwebs, and that seems about right.

If you do that, I think DeVeDe will work, more or less, although I found that fast forward did not work on the DVDs (double and triple fast work all right).

---

### Post by poltr1 on 2011-04-26
Thank you, ron999!  

I had a series of mp4 files that I wanted to copy to a DVD for offline watching.  I tried using Pitivi to string them together, but the rendering was going to take more than 24 hours, so I gave up on that method.

For each of the mp4 files, I repeated steps 1 and 2, and did step 3 only once.  Total rendering/conversion time for about an hour's worth of video was about 30 minutes.

Step 4 was to fire up CD/DVD creator, copy the AUDIO_TS and VIDEO_TS directories, and burn.  But that step's a given.  :-)

---

### Post by poltr1 on 2011-04-26
Forgot a small detail with dvdauthor.  If you want a title with multiple chapters, you need to specify the chapters of a title on the same command line.  Example:

dvdauthor -o DVD/ -t foo.mpg bar.mpg xyzzy.mpg plugh.mpg

---

### Post by kelt65 on 2011-04-26
> **skywatcher said:**
> Is there no way that I can simply convert ogg theora to the correct format for a video DVD? I tried ManDVD, but it overflows the screen and I can't see the buttons at the bottom. I also tried Devede, but I get an error that says "... it seems to be a bug of Mencoder". Besides, both these programs, when I install them from the Ubuntu Software Center, require that I remove certain lib installations. Why?

Pitivi isn't for making DVD's but video files. Devede can take any video file and create a DVD iso which you can in turn burn to a DVD. Not sure but devede might be able to actually burn the disk as well.

---


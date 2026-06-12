---
title: "A good simple tutorial for WinFF?"
date: 2010-04-07
forum: Multimedia Software
---

### Post by Roger Allott on 2010-04-07
I've tried to use WinFF a number of times but keep failing to get it to do what I want it to do (i.e. convert a video file from one format to a different format).

There are numerous help pages out there on the interweb, but they're about as useful as a chocolate teapot. What I want is a tutorial.

I don't want to know what I **can** enter into the various fields in 'Additional Options' - I want to know what (if anything) I **should** enter into those fields.

I don't want to know which formats I can convert a file to - I want to know which format(s) would be best to convert to (i.e. losing the minimum amount of video or audio resolution).

For example, I have an rmvb file that I would like to convert to a more widely supported format, such as avi, mpeg-4 or even wmv. But when I run it through WinFF, leaving all the option fields blank (default), I just end up with a terminal screen doing something for a few hours and at the end I get a file with the right filename but of exactly zero bytes.

Anyone got any ideas?

---

### Post by ron999 on 2010-04-07
Hi
Ideas?
Well before you try and do the conversion, make sure that WinFF will _play_ your rmvb file first. If it won't play it then it (probably) won't be able to convert it either.

---

### Post by FakeOutdoorsman on 2010-04-07
Perhaps you need to enable additional encoders in FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by LuridCinema on 2010-04-07
I recommend ffmpeg .... I have saved all useable input parameters and saved them for future reference.

Below is some of the commands that have worked for me
```

ffmpeg -i 100_0013.mov -target ntsc-dvd -s 1280x720 file.mpeg2video

ffmpeg -i uuuus.mov -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre max -crf 18 -r 29.97 -threads 0 movie.mp4


ffmpeg -i vid5.mov -target ntsc-dvd -s 1280x720 -r 59.94 test-88.mpeg2video

 ffmpeg -i test1.mov -r 29.97 -sameq test2.mov
------------------------------------------------------------------------------
COMBINE audio & Video
ffmpeg -i spaunlimit222.ac3 -i spaunlimit222.m2v -sameq spa-YES.mpg  << merged audio & video

-----------------------------------------------------------------------------
ffmpeg -i spaunlimit.mov -s 1280x720 -sameq -ar 44100 spaunlimit720.flv  << lowered 1920x108 to 1280x720 YOUTUBE LIIIKE !!!

ffmpeg -i tjet2-youtube.mov -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -wpredp 0 -s 1280x720 -crf 24 -threads 0 tjet2.mp4
 YOUTUBE LIIIKE !!!


mencoder -oac copy -ovc copy -idx -o output.avi video1.avi video2.avi video3.avi   << concatenate  3 files into 1


ffmpeg -i spa-logo2.mov -s 900x100 -sameq -ar 44100 -ab 192 spa-logo2.swf

png2swf -o file6.swf -r 24 *.png   << rip vid into png
ffmpeg -f image2 -i %03d.jpeg -r 06 -sameq foo592.avi   << 3 digit jpegs to avi

-ss 0:10:12 -t 0:05:30   TIME START & Duration


ffmpeg -i spa.mov -deinterlace -pix_fmt yuv420p -g 15 -qmin 3 -maxrate 628000 -bufsize 628k -async 50 -vcodec wmv2 -b 500000 -r 29.97 -s 740x480 -acodec wmav2 -ar 44100 -ac 2 -ab 128k spa.wmv
ABOVE worked for .MOV to wmv for Zune

ffmpeg -i mig.avi -sameq -s 720x480 -r 29.97 mig.mov  <<< FIRST rip to .MOV  THEN to .WMV ABOVE

ffmpeg -i nhc.flv -sameq -s 400x272 -r 29.97 nhc.mov   <<< FIRST rip to .MOV  THEN to .WMV ABOVE



ffmpeg -i FILE.flv -acodec aac -ac 2 -vcodec mpeg4 -s qcif -b 128kb -r 14.985 FILE.3g2

-------------------------------------------------------------------------------------------------------
EXTRACT PNG files
ffmpeg -i 30255.wmv -r 30 -t 00:00:30 -f image2 images%05d.png  <<< 5 zeros  do it for 30 seconds
ffmpeg -i 30255.wmv -sameq -r 30 -ss 0:00:12 -t 00:00:02 -f image2 images%05d.png  << do it for 2 secs  start at 12 sec

```

---

### Post by Roger Allott on 2010-04-08
> **ron999 said:**
> Hi
Ideas?
Well before you try and do the conversion, make sure that WinFF will _play_ your rmvb file first. If it won't play it then it (probably) won't be able to convert it either.

Yes, it plays the vid fine.

---

### Post by Roger Allott on 2010-04-08
> **FakeOutdoorsman said:**
> Perhaps you need to enable additional encoders in FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Yes, I had all of those extras.

---

### Post by Roger Allott on 2010-04-08
> **LuridCinema said:**
> I recommend ffmpeg .... I have saved all useable input parameters and saved them for future reference.


But that still doesn't help me to know what parameters I **should** use for different circumstances.

---

### Post by littlepeon on 2010-04-08
your question is way to vague...essentially you are asking for a simple guide to brain surgery.
winff--which is simply a frontend to ffmpeg has way to many options to TELL you which is the right one for every situation...it simply comes with simple presets for the most common ones.
your situation is unique your videos are encoded with rmvb. few people use this option--the most common files are encoded with divx/xvid, h.264(mkv,et. all), or mpeg--(most people like to use open, common ways for encoding--not proprietary codes like Real Media or Quicktime which were common in the late 90's)

what do you want your final format to be??? 
if you simply google convert rmvb to xxx using ffmpeg(xxx being mpeg, divx, avi, mkv, etc) you will find many ways to do this and explanations for the command arguments 
all you need to do then in winff is to set a preset that will do this for you...

if you need help with what the different argument to the ffmpeg command will do, you can ask specific questions here or google..there are many different sites dealing with video conversion....the man page for ffmpeg is 1000 lines long--there are MANY options you can have.

however there is no "idiots guide to converting video using linux---using winff"

-peon

---


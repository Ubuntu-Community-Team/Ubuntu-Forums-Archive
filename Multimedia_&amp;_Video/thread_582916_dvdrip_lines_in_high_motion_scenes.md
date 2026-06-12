---
title: "dvd::rip lines in high motion scenes"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by cyberdemon on 2007-10-20
I have been ripping DVD with windows for years. I have just not decided to use a linux counterpart. The tools I have used in windows were dvd decryptor and autogk (with all tools associated)

I have tried several linux programs that accomplish the same task. (mainly front ends to mencoder) 

They all produce a video file that when played back results in lines through any motion.


Reading online the general consensus is that dvd::rip is the best program for encoding dvd's in linux. Therefore this is the program I have chosen to use. 


I Installed:

**mencoder** (cvs) using instructions from [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)
[B]
libdvdcss2[/B]
**w64codecs**
**all gstreamer plug-ins**
**dvd::rip** and all required programs



The settings I have used in dvd::rip are 

xvid
frame rate 23.976
2 pass encoding
target size 800MB
ac3 audio
no deinterlacing

Playing the DVD in totem, xine, or mplayer looks great.

Now every DVD I have encoded has these white line during any motion. especially during more active scenes. I have tried may different settings (increasing file size, mp3 audio) and all resulting video output results in the same poor quality video.

I don't know what else to do to get a high quality video from dvd::rip has anyone else experienced problems like this and if so do you have any solutions?

I should also mention that playing a video file encoded from autogk or downloaded from the net plays flawlessly.


Thanks in advanced for any help.

I have deleted all of the encoded files otherwise I would post a screen shot. I currently trying the same encode using smart deinterlacing to see if that might solve the problem. If not I will post a screen shot.

---

### Post by ellgor on 2007-10-21
Hi,

Haven't got the same problem as you have but have you got the latest release of dvdrip, the latest being 0.98.1, which comes with all dependencies included.
It can be found at  >  exit1.org/dvdrip  <  and it is a great improvement on an already good program, hope this helps.

Regards, Ellgor.

---


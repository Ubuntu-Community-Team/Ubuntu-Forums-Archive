---
title: "avi to mpeg (how?)"
date: 2008-10-04
forum: Multimedia Software
---

### Post by serpentine_bull on 2008-10-04
after about a week of trying to burn through countless man files and forum posts, i'm ready to smash things. lots of things. 

I've set up a dlna server using Ushare, which works beautifully with mpeg files, but refuses to play avi files (on my ps3, which doesn't support avi files) naturally, i hit google and looked for a conversion tool. FFmpeg will convert files, but the resolution is terrible and the audio loses sync after about 15 minutes. The videos i'm trying to convert are encoded in xvid video and mp3 audio; I compiled ffmpeg with xvid support and mp3lame support. Avidemux and mencoder are more difficult to find decent conversion commands for. is there some awesome program that I'm missing, or is failure to convert avi to mpeg under linux with reasonable ease just another reason i should give up, hate life, and use windows?

I know, since i'm all about linux, i'm supposed to be calm, collected, cool, and able to solve problems with a relentless observation/evaluation/method_adaptation/repeat method, but at this point i just want to smash things.




here's my ffmpeg command:
```
ffmpeg -i x.avi -ab 128k -s 1280x1024 x.mpg
```
(the source file has a 139 audio bitrate, the same audio sampling rate as ffmpeg defaults to, and the resolution is retarded low at 512x384. all the same, video is sketchy at 1280x1024)

the mencoder command
```
mencoder x.avi -of mpeg -ovc lavc -lavcopts vcodec=mpeg1video -oac copy other_options -o output.mpg
```
(returns error 
```
videocodec: libavcodec (512x384 fourcc=3167706d [mpg1])
[mpeg1video @ 0x8814710]MPEG1/2 does not support 2997/125 fps
Could not open codec.
FATAL: Cannot initialize video driver.
```)

mencoder was installed via apt-get, ffmpeg was custom installed from the source. Should I ./configure mencoder with additional codec support? hammer through avidemux and try to figure out something there? smash more things? My problem solving skills are exhausted.....(except for smashing things, of course.)

---

### Post by guatebus on 2008-10-21
* bump *

This question is out of my league (linux newbie) but I have the same problem.  I have a .avi that I want to convert to .mpeg so please, someone help??

---

### Post by owain123 on 2008-10-21
So you have installed ubuntu-restricted-extras? Mplayer cannot  find the right codec for some reason, might be that its looking in the wrong folders.

How about opening an avi and an mpeg with mplayer in terminal,

eg, mplayer /home/user/videos/video.mpeg  

If it can't find the right codec, it will say so in the terminal, and show the folders its been looking in. So download the codec and put it in the folders Mplayer looks in and give it another try.

Thats my only guess anyway, hope it helps.

---

### Post by cor2y on 2008-10-21
what you could try is forcing a specific frame rate for the video output that seems to be the problem.
Mencoder is saying for mpeg1 that the frame rate the avi has is not a compliant one for that codec.
So here is what you can try and let us know if it works
```

mencoder x.avi -of mpeg -ovc lavc -lavcopts vcodec=mpeg1video -oac copy -ofps 30000/1001 -o output.mpg 
```Although i would set the audio for something else to be mpeg1 compliant if its mp3 audio.
Something like this
```
mencoder x.avi -of mpeg -ovc lavc -lavcopts vcodec=mpeg1video -oac lavc -lavcopts acodec=mp2:abitrate=224 -ofps 30000/1001 -o output.mpg
```

---

### Post by haydnc on 2008-10-21
I just use ffmpeg on its own to to the conversion for me.

Have you tried using the pre-configured settings that are built in?

Try:
```
ffmpeg -i input.avi -target pal-dvd output.mpg
```

If you're in ntsc country you can use ntsc instead of pal. I'm afraid I can't recall which is the default.

I've not had any serious sync problems doing it this way unless there was something **very** unusual about the way the avi was encoded in the first place.

---

### Post by guatebus on 2008-10-27
I found these very helpful instructions

[http://www.pelogo.org/index.php/blog/show/Como-convertir-videos-avi-a-DVD-con-Linux.html](http://www.pelogo.org/index.php/blog/show/Como-convertir-videos-avi-a-DVD-con-Linux.html)

hope it works. did for me.

---

### Post by jacobw.uk on 2008-10-27
Have you tried using VideoLAN Client to transcode the AVI to MPEG?

---


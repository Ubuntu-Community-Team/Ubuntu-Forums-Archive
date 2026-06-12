---
title: "How to Convert avi to mpeg-4 for Playstation 3"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by drews_blunted on 2007-03-06
I recently bought a Playstation 3 and was sad to see that it only supported playback of mpeg-4 and did not support divx, avi, or wmv. Most of my media on my MythTV box is encoded to .avi divx files. What i am curious about is how can i convert these avi files to mpeg-4 for playback on my playstaion 3's XMB(playstaion 3's user interface). I know there is some programs used for doing this type of task for the Playstaion Portable but i have not seen any designed for Playstaion 3. Is there a program like this i just dont know about? Or what command can i use for ffmpeg to convert this file? Any help would be apreciated. Thanks
:guitar:

---

### Post by crispy_420 on 2007-03-07
DivX and Xvid are both standard avi's. Sound like you just need the proper codec. From what I found you need to use H.264 codec.

Here are a link:

[http://www.cdrinfo.com/Sections/News/Details.aspx?NewsId=18779](http://www.cdrinfo.com/Sections/News/Details.aspx?NewsId=18779)

[Good news is that linux can be installed on it.]("http://en.wikipedia.org/wiki/PlayStation_3_Linux")

---

### Post by disturbedite on 2007-03-08
> **crispy_420 said:**
> DivX and Xvid are both standard avi's. Sound like you just need the proper codec. From what I found you need to use H.264 codec.

Here are a link:

[http://www.cdrinfo.com/Sections/News/Details.aspx?NewsId=18779](http://www.cdrinfo.com/Sections/News/Details.aspx?NewsId=18779)

[Good news is that linux can be installed on it.]("http://en.wikipedia.org/wiki/PlayStation_3_Linux")

this is correct, i'm sure.  *avi is just the container, it isn't a format itself*.  apparently the ps3's media decoding does not include divx or xvid, but does have h264 decoders.  (if not all) most video editing/converting apps can convert/export to h264.  i don't know what container format you need to use, avi or mp4, but check that out too.

---

### Post by drews_blunted on 2007-03-08
Is there a program i can use to convert my current movies to H.264 codec? Im not sure how to do this my previous attempts with ffmpeg did not work.

This is what i have been trying to get work for me:
Sadly i get this error from my ffmpeg:
ffmpeg: error while loading shared libraries: libmp3lame.so.0: cannot open share

Ive read a number of other posts on the forum and it seems other people are having similar issues with ffmpeg

```
ffmpeg -y -i InputMOVIE.avi -title "Movie Name" -bitexact -vcodec xvid -s 640x480 -r 29.97 -b 1500 -aspect 4:3 -acodec aac -ac 2 -ar 24000 -ab 64 -muxvb 768 OutputMovie.mp4
```

below i jusr posted some more info from the above link.

**Supported Formats for Playstation 3**

VIDEO:
MPEG-1, MPEG-2 (PS,TS), H.264/MEPG-4 AVC, MPEG-4 SP

MUSIC:
ATRAC (.oma .msa .aa3), AAC (.3gp .mp4), MP3 (.mp3), WAV (.wav)

IMAGES:
JPEG, GIF, PNG, TIFF

---

### Post by disturbedite on 2007-03-08
try avidemux.

BTW:  nice to see another infowarrior on the forum!  don't want no shackles on me, down with big brother!

---

### Post by drews_blunted on 2007-03-09
Yep, glad to see someone notices my link. Good stuff, hopefully the ubuntu community is open enough. :) Ive tryed using avidemux but im runnning feisty and it the program is not stable so i will have to wait untill that fix's itself or becomes stable around the release. Im still trying to get ffmpeg to work, but im having some problems mainly im guessing due to feisty.

---

### Post by disturbedite on 2007-03-09
in regards to avidemux; i'm on feisty too and it works fine.  i haven't seen a single stability issue.  i use it all the time.  i kinda consider it the virtualdub of linux, but better in a lot of ways.

btw i'm listening to alex jones as i'm typing!

---

### Post by OmniCloud on 2007-03-09
I'm also trying to get my Naruto avi. files on my PS3 in a better quality. 

So far, all I've got to work is a front-end interface for ffmpeg called WinFF. The only one that works is Mpeg-2 and the quality is horrible compared to my PC...

I'm looking into something called Devede now? 

Is there really no way to get quality vids on your PS3 man?? The ones that you download from the store look freakin awesome!!

---

### Post by OmniCloud on 2007-03-09
HEy!! with some experimenting, I've actually got some better quality stuff here...I used the Winff and changed the settings a bit. 

First I made sure the video was in 16:9 aspect ration
then change the resolution to 720X480 

Nice and subtle differences in the quality. my TV is 720p but when I put in that resolution, (1280X720) I don't get playback on my PC or my PS3...

How much higher can I go from 720X480? and what numbers should I enter in the resolution when converting?

---

### Post by biggmatt on 2007-03-23
[QUOTE=OmniCloud;2274025]

So far, all I've got to work is a front-end interface for ffmpeg called WinFF. The only one that works is Mpeg-2 and the quality is horrible compared to my PC...
/QUOTE]

The ffmpeg from the Ubuntu repositories is majorly cut down for legal reasons. You can get a deb of an optimized ffmpeg here: [http://skulboxx.com/Ubuntu/sbx/]("http://skulboxx.com/Ubuntu/sbx/")

---

### Post by wolvorine4424 on 2007-04-04
Thank you...

I was looking for something like this.

It also converts VOB files from the DVD to MPEG4 for PS3... Nice
CPU Killer. This program Rapes my CPU... :lolflag:

---

### Post by the lost boy on 2008-06-26
wait !!!!!!!!!!!!!

the ps3 can play .avi files!!!!
they just don't show up right away. when you put in a media device like a memory stick or dvd you have to press the triangle button and click on display all. you will then see the folder or .avi file. when you click on the .avi file it will play.
 
have fun.

---


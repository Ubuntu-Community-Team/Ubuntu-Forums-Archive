---
title: "PS3 &amp; mkv"
date: 2012-04-04
forum: Multimedia Software
---

### Post by Condor Cluster on 2012-04-04
I've got a movie in mkv format that I really want to plays on my TV via PS3. 

Is it possible to change the mkv into avi or mp4 (something the PS3 will read), without losing (too much) quality?

Ideally, if its possible with something like vlc.

Thanks.

---

### Post by ron999 on 2012-04-04
Hi
Do research to find out what formats can be played by your PS3.
And use MediaInfo to find out what's inside the mkv file.

Then maybe you will be able to to convert it.

---

### Post by Condor Cluster on 2012-04-04
Well, from my understanding, mkv is just the container for the video/audio/subs, so in theory I could change the container to avi/mp4 and not touch the video/audio/subs?

PS3 definitely won't play mkv, I think if I change the container it might work though.

The other way round this would be to stream it from a laptop to PS3, but that sounds kinda complicated...

---

### Post by shantiq on 2012-04-04
ok these are the [formats ]("http://manuals.playstation.net/document/en/ps3/current/video/filetypes.html")


> Types of files that can be played

The following types of files can be played under  (Video).
Memory Stick Video Format
- MPEG-4 SP (AAC LC)
- H.264/MPEG-4 AVC High Profile (AAC LC)
- MPEG-2 TS(H.264/MPEG-4 AVC, AAC LC)
MP4 file format
- H.264/MPEG-4 AVC High Profile (AAC LC)
MPEG-1 (MPEG Audio Layer 2)
MPEG-2 PS (MPEG2 Audio Layer 2, AAC LC, AC3(Dolby Digital), LPCM)
MPEG-2 TS(MPEG2 Audio Layer 2, AC3(Dolby Digital), AAC LC)
MPEG-2 TS(H.264/MPEG-4 AVC, AAC LC)
AVI
- Motion JPEG (Linear PCM)
- Motion JPEG (&#956;-Law)
AVCHD (.m2ts / .mts)
DivX
WMV
- VC-1(WMA Standard V2)


so using ffmpeg try  


```
 ffmpeg -i originalfile.mkv  -b  4000k -ab 192k finalfile.mp4
 
```

this will give you a decent quality copy   [if there is a sub it becomes more involved]

---

### Post by SeijiSensei on 2012-04-04
For a one-off project, converting with ffmpeg or mencoder to .mp4 is probably the best choice.  If you need to preserve multiple audio tracks or subtitles, you'll need to do some research into the converter you choose.  If you prefer using a GUI interface, [Handbrake]("http://handbrake.fr/details.php") can do conversions like these.  You can install it from this [PPA]("https://launchpad.net/~stebbins/+archive/handbrake-releases").

If you expect to be watching other Matroska files on your PS3, installing [ps3mediaserver]("http://code.google.com/p/ps3mediaserver/") on a computer is the better long-term option.

---

### Post by evilsoup on 2012-04-04
> Well, from my understanding, mkv is just the container for the  video/audio/subs, so in theory I could change the container to avi/mp4  and not touch the video/audio/subs?

PS3 definitely won't play mkv, I think if I change the container it might work though.

Your understanding is correct.
Using ffmpeg, and assuming that all the codecs in your .MKV are compatible with the .MP4 container (they probably are), use

ffmpeg -i input.mkv -acodec copy -vcodec copy output.mp4

This will take only slightly more time than a cp operation, and you will not lose any quality. If the files have subtitles, things get a little more complicated (-scodec copy should work, but sometimes it doesn't).

Hope this helps.

---

### Post by dwn99 on 2012-04-05
Hey, if you didn't already know this, you can install pms-linux.  It stands for PlayStation Media Server if memory serves.  You install it on your linux server, tell it which folders to share, then you can access it from your PS3. (I think you have to enable media server sharing on the PS3, but you've probably already done that.)  

PMS can do conversion on the fly of .mkv files in most cases.  I'm not saying it's ideal.  It's hard to fast forward, etc.  But it does usually work.  You just have to go to the Transcode folder when you are navigating PMS from your PS3.

Hope that helps.  If not, please ignore.  :)

---

### Post by Lemuriano on 2012-04-05
Whenever I need to convert mkv to mp4, handbrake works like a charm.

---

### Post by Condor Cluster on 2012-04-12
Yeah, I tried that PS3 Media Server program on a vista laptop. Once the PS3 media server is up and running, it basically allows you to 'browse' the files and folders on the laptop via the Playstation. It seems to convert and stream movies across quite well.

I think you can get the program for linux too, but the Windows version is working fine (it did make me update to Java 7 though)

Maybe in the future, VLC 2.0 will be able to do the same with PS3/360s...

---


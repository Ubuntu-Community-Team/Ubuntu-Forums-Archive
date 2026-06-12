---
title: "ffmpeg converts: video stream too slow.. plz help!"
date: 2009-07-13
forum: Multimedia Software
---

### Post by abhigyan91 on 2009-07-13
hey i tried converting a music vid in mkv format, vcodec=H264, acodec=mp3, r=24fps, to
a 3gp format using acodec=libfaac, vcodec H263 and r=24fps, i got an output in which the video is too slow, as in the last 30 seconds contains no audio as there is nothing left to play but the video keeps goin on. Since the fps is the same in both files, could the vcodec be a problem?

also plz tell me which codecs are suported by the following containers:
avi, mkv, flv, 3gp, mpg

i got the full listing of all codec supported by 
```
ffmpeg -formats
```

but this gives a gigantic list in which not all of them work.

for example ,i cant convert using the mpeg codec, also, to get an mp3 audio stream, i can't just use ```
-acodec mp3
```, i am sure there are many more inconsistencies that i havn't come across since i have not yet experimented with all the codecs in the list. any pro ffmpeg-ers.. plz help.. i thot ffmpeg was sups to be a classy utility, to me it seems like a big hassle!!

---

### Post by Keith Hedger on 2009-07-13
Have you tried letting ffmpeg select the various codecs for you, if you just give a command like:```
ffmpeg -i somefile.mkv outfile.3gp
```
ffmpeg is horrendously complex and i usually just let it decide for itself.

---

### Post by SuperSonic4 on 2009-07-13
> **abhigyan91 said:**
> hey i tried converting a music vid in mkv format, vcodec=H264, acodec=mp3, r=24fps, to
a 3gp format using acodec=libfaac, vcodec H263 and r=24fps, i got an output in which the video is too slow, as in the last 30 seconds contains no audio as there is nothing left to play but the video keeps goin on. Since the fps is the same in both files, could the vcodec be a problem?

also plz tell me which codecs are suported by the following containers:
avi, mkv, flv, 3gp, mpg

i got the full listing of all codec supported by 
```
ffmpeg -formats
```

but this gives a gigantic list in which not all of them work.

for example ,i cant convert using the mpeg codec, also, to get an mp3 audio stream, i can't just use ```
-acodec mp3
```, i am sure there are many more inconsistencies that i havn't come across since i have not yet experimented with all the codecs in the list. any pro ffmpeg-ers.. plz help.. i thot ffmpeg was sups to be a classy utility, to me it seems like a big hassle!!

I would not specify the frame rate unless you need to change it, if left as is then it will simply copy it from the input. Also to get mp3 you need a different codec for it:

```
ffmpeg -i somefile.mkv -vcodec h264 -s 320x240 -aspect 4:3 -sameq -acodec libmp3lame -ac 2 -ab 128k output.3gp
```

*Use **-vcodec copy** to force copying of all video data - this will override the commands below*

[list]
[*]**-vcodec h264** means encode in h264 (the other one I use is mpeg4)
[*]**-s 320x240** means size of 320x240 
[*]**-aspect 4:3** means force a 4:3 aspect ratio (320/240 = 4/3)
[*]**-sameq** means same quality (use **-b <num>k** to pick a bitrate
[/list]

*Like above you can use **-acodec copy** to copy the audio and override the settings below*

[list]
[*]**-acodec libmp3lame** means encode to mp3 (it may also be liblamemp3) but another one is libfaac to encode to m4a
[*]**-ac 2** means dual channels
[*]**-ab 128k** means 128kbps audio
[/list]

ffmpeg is a very classy utility and I am the envy of my windows friends because I can choose how to encode (for example I have a high quality video but sacrifice filesize because it is not a problem on a 2gb memory card). You just have to learn how to use it and for that it's best to look in the man page and pass whichever flags look cool xD

---

### Post by FakeOutdoorsman on 2009-07-13
> **abhigyan91 said:**
> hey i tried converting a music vid in mkv format, vcodec=H264, acodec=mp3, r=24fps, to
a 3gp format using acodec=libfaac, vcodec H263 and r=24fps, i got an output in which the video is too slow, as in the last 30 seconds contains no audio as there is nothing left to play but the video keeps goin on. Since the fps is the same in both files, could the vcodec be a problem?

also plz tell me which codecs are suported by the following containers:
avi, mkv, flv, 3gp, mpg

You may find this useful: [Comparison of container formats](http://en.wikipedia.org/wiki/Comparison_of_container_formats) [wikipedia.org]

> i got the full listing of all codec supported by 
```
ffmpeg -formats
```

but this gives a gigantic list in which not all of them work.

for example ,i cant convert using the mpeg codec, also, to get an mp3 audio stream, i can't just use ```
-acodec mp3
```, i am sure there are many more inconsistencies that i havn't come across since i have not yet experimented with all the codecs in the list. any pro ffmpeg-ers.. plz help.. i thot ffmpeg was sups to be a classy utility, to me it seems like a big hassle!!

Default FFmpeg in the Ubuntu repository does not have restricted encoders enabled, so you have to do it manually but it isn't too hard:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283) [ubuntuforums.org]

---

### Post by abhigyan91 on 2009-07-14
@FakeOutdoorsman: Thank you for the wikipedia site, exactly what i needed. I had already installed the unstripped version of ffmpeg(option B in the link you provided), though still, i am not able to acess some codecs like mpeg and mpeg4.

@supersonic:  Thanks for the mini-tutorial, i din;t know libmp3lame was the name for encoding in mp3. 

however, i still am not able to convert properly, the video is too slow, making the video go on even while the audio stops. Also the quality is not the same even if i use -sameq..:( I am planning to reinstall ffmpeg and compile it from the source code itself, maybe that will help.

---


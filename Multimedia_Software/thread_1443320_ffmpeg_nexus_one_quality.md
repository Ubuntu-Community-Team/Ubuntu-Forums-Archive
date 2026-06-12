---
title: "ffmpeg nexus one quality"
date: 2010-03-30
forum: Multimedia Software
---

### Post by snares on 2010-03-30
I have a nexus one that I would like to get some videos on. I have found a few command line codes to put in to convert files to mp4s. CLI ffmpeg ahs worked the best. I have tried Handbrake, WinFF, ViVe noe of which have worked. I'll stick with cli ffmpeg. But when I convert it the quality is lacking. Lots of artifacts and sound is horrible IMO. One time there was no audio. What am I doing wrong and what do I put in to improve the quality.

```
ffmpeg -i input.avi -s 800x480 -vcodec mpeg4 -b 256000 -acodec libfaac -ac 2 -ar 48000 -r 13 -ab 32000 -aspect 16:9 output.mp4
```

```
ffmpeg -i input.avi -s 800x480 -vcodec mpeg4 -acodec libfaac -ac 2 -ar 16000 -r 13 -ab 32000 -aspect 16:9 output.mp4
```

looking at the -h of ffmpeg I have figured out what most of the operands means but not sure what to change or add in. Thanks for the help.

cheers
snares

---

### Post by FakeOutdoorsman on 2010-03-31
It appears that the [Nexus One](http://www.google.com/phone/static/en_US-nexusone_tech_specs.html) can handle H.264 video.  Unfortunately, I couldn't find any more detailed specifications on any limitations so some trial and error might be required.  I prefer using *-vcodec libx264* instead of *-vcodec mpeg4* because I can get better results.  Below are some example commands that will encode to H.264 video and AAC audio.  You will need to enable these encoders in FFmpeg if you haven't already:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

**profile High, level 3.1**
```
ffmpeg -t 10 -i input.avi -acodec libfaac -ab 128k -vcodec libx264 -vpre hq -crf 24 -threads 0 output1.mp4
```

**profile Main, level 3.1**
```
ffmpeg -t 10 -i input.avi -acodec libfaac -ab 128k -vcodec libx264 -vpre hq -vpre main -crf 24 -threads 0 output2.mp4
```

**iPod 640 preset**
```
ffmpeg -t 10 -i input.avi -acodec libfaac -ab 128k -vcodec libx264 -vpre hq -vpre ipod640 -f ipod -crf 24 -threads 0 output3.mp4
```

I added a *-t 10* to encode only 10 seconds of the input so you don't have to encode a potentially large input.  I didn't add a frame size (*-s*) because I don't know anything about your source video.  If none of these examples work I have a few other ideas you can try.

---

### Post by snares on 2010-03-31
You are right on the quality. It is much better. But it still doesn't play on the nexus. Dont know why. Tech specs says H.264. I wonder what the decoded next to it means. All well. Any thoughts? I got all day tomorrow since the NorthEast is flooded. So I guess I can get this working \\:D/

---

### Post by rossmoore on 2010-03-31
Hey, thought I'd drop in because I have a Nexus One, Ubuntu Karmic and have been watching videos on it.

I use Handbrake to transcode videos. I created a new profile based on the iPhone profile that comes with the default installation of Handbrake. I then altered the resolution to 800*480 (or whatever it is, I don't have the settings in front of me) and played with the quality setting to get the right balance of quality and size. I currently use a setting of "24" I think, which seems fine - but YMMV.

The videos play both in Gallery and in Meridian (another popular video and music player, available in the android marketplace).

---

### Post by rossmoore on 2010-03-31
One other thing - Handbrake creates "m4v" files. This is where my detailed knowledge of video containers runs out, but perhaps there is a small difference between m4v files and mp4 files? I know they're very similar, but I think there might be differences...

[Edit] [http://en.wikipedia.org/wiki/MPEG-4_Part_14](http://en.wikipedia.org/wiki/MPEG-4_Part_14)
This indicates that the files might be just raw bitstreams rather than some kind of container - maybe that's the difference? Anyway, let me know how you get on with those Handbrake settings, or if you need any more detail.

---

### Post by snares on 2010-03-31
I try to get Handbrake to work but I can't click the start button to begin the coversion. All I can do is select a source video thats it. Everything else is grayed out so I cant click it. This was what I tried first. Thanks for the suggestion though.

cheers
snares

trying out HandbrakeCLI now. It's coverting I think. But I'm really tired. So we'll findout if it worked tomorrow. figures crozzzzzzzzed.

---

### Post by rossmoore on 2010-03-31
I didn't know HandbrakeCLI worked on Gnome. That's good to know! Strange that you have everything greyed out - you know it takes a little while to analyze the source before allowing you to convert, I presume? Have you tried running it from the console (gtb is the command) to view any error messages?

I hope everything works overnight!

---

### Post by snares on 2010-03-31
HandbrakeCLI worked! Much better quality than the mpeg4 ones. Thanks.

cheers
snares

---

### Post by FakeOutdoorsman on 2010-03-31
Can you show your HandbrakeCLI command?  I'd like to analyze the output to see why FFmpeg failed.  Also, rossmoore makes a good point with the *m4v*.  FFmpeg does create a different output when the only difference in the command is the output file name:
```
ffmpeg -t 10 -i input.mkv -an -vcodec libx264 -vpre hq -crf 26 -threads 0 shavedape.m[p4|4v]
```
```
$ md5sum shavedape.m4v shavedape.mp4 
ff2871b33369104033d7b58ca1f36759  shavedape.m4v
298fcb6229df9e66965040cdee044cf8  shavedape.mp4
```
I'd still like to get this working with FFmpeg, but unfortunately I don't own a Nexus One.

---

### Post by snares on 2010-03-31
```
HandBrakeCLI -i ~/Videos/Benders_Game.avi -o ~/Videos/Nexus/Benders_Game.mp4  -e x264 -q 0.589999973773956 -a 1 -E faac -B 128 -R 48 -6 dpl2 -f mp4 -Y 480 -X 800 -m -x level=30:cabac=0:ref=2:mixed-refs:analyse=all:me=umh:no-fast-pskip=1
```


I took the command from 
[http://trac.handbrake.fr/wiki/BuiltInPresets#iphone]("http://trac.handbrake.fr/wiki/BuiltInPresets#iphone")

the only thing I changed was adding in ```
-Y 480 -X 800
``` 

for the resolution on the Nexus One. I'd like to try and get FFMpeg to work as well. If you leave the code you want to try I'll run it and tell you the results.

Video quality is great but the sound lags from time to time. Perhaps bringing down the resolution will help this. I'll have to try it.

---

### Post by FakeOutdoorsman on 2010-03-31
Apparently Handbrake is outputing High Profile, Level 3.0:
```
$ mediainfo handbrake.mp4 
General
Complete name                    : handbrake.mp4
Format                           : MPEG-4
Format profile                   : Base Media / Version 2
Codec ID                         : mp42
File size                        : 31.6 MiB
Duration                         : 1mn 48s
Overall bit rate                 : 2 442 Kbps
Encoded date                     : UTC 2010-03-31 21:46:00
Tagged date                      : UTC 2010-03-31 21:46:47
Writing application              : HandBrake rev2965 2009112799

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L3.0
Format settings, CABAC           : No
Format settings, ReFrames        : 2 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 1mn 48s
Bit rate mode                    : Variable
Bit rate                         : 2 311 Kbps
Width                            : 800 pixels
Height                           : 336 pixels
Display aspect ratio             : 2.35:1
Frame rate mode                  : Variable
Frame rate                       : 23.976 fps
Minimum frame rate               : 23.810 fps
Maximum frame rate               : 24.390 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.359
Stream size                      : 29.9 MiB (95%)
Writing library                  : x264 core 79
Encoding settings                : cabac=0 / ref=2 / deblock=1:0:0 / analyse=0x3:0x133 / me=umh / subme=7 / psy=1 / psy_rd=1.0:0.0 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=0 / 8x8dct=1 / cqm=0 / deadzone=21,11 / chroma_qp_offset=-2 / threads=12 / nr=0 / decimate=1 / mbaff=0 / constrained_intra=0 / bframes=3 / b_pyramid=0 / b_adapt=1 / b_bias=0 / direct=1 / wpredb=1 / wpredp=2 / keyint=240 / keyint_min=24 / scenecut=40 / rc_lookahead=40 / rc=crf / mbtree=1 / crf=20.9 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / ip_ratio=1.40 / aq=1:1.00
Encoded date                     : UTC 2010-03-31 21:46:00
Tagged date                      : UTC 2010-03-31 21:46:47
Color primaries                  : BT.709-5, BT.1361, IEC 61966-2-4, SMPTE RP177
Transfer characteristics         : BT.709-5, BT.1361
Matrix coefficients              : BT.709-5, BT.1361, IEC 61966-2-4 709, SMPTE RP177

Audio
ID                               : 2
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 1mn 48s
Bit rate mode                    : Variable
Bit rate                         : 128 Kbps
Maximum bit rate                 : 176 Kbps
Channel(s)                       : 2 channels
Channel positions                : L R
Sampling rate                    : 48.0 KHz
Stream size                      : 1.66 MiB (5%)
Encoded date                     : UTC 2010-03-31 21:46:00
Tagged date                      : UTC 2010-03-31 21:46:47

Text
ID                               : 3
Format                           : Apple text
Codec ID                         : text
Duration                         : 1mn 48s
Bit rate                         : 2 bps
Stream size                      : 23.0 Bytes (0%)
Encoded date                     : UTC 2010-03-31 21:46:00
Tagged date                      : UTC 2010-03-31 21:46:47
```
Try this:
```
ffmpeg -t 10 -i input.avi -an -vcodec libx264 -vpre hq -crf 24 -threads 0 -level 30 -s 800x480 output4.mp4
```
If that doesn't work then try:
```
ffmpeg -t 10 -i input.avi -an -vcodec libx264 -vpre hq -crf 24 -threads 0 -level 30 -vtag mp42 -s 800x480 output5.mp4
```
I removed the audio encoding from these examples to reduce the points of failure.  If the video works, then we can move on to the audio.

---

### Post by snares on 2010-03-31
I tried both still nothing. I installed MediaInfo so I could post information for you. The output for the second command you gave me is this:
```
General
Complete name                    : /home/snares/Videos/Nexus/Benders_Game_2.mp4
Format                           : MPEG-4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 1.30 MiB
Duration                         : 10s 10ms
Overall bit rate                 : 1 088 Kbps
Writing application              : Lavf52.31.0

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L3.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 10s 10ms
Bit rate mode                    : Variable
Bit rate                         : 1 085 Kbps
Width                            : 800 pixels
Height                           : 480 pixels
Display aspect ratio             : 16:9
Original display aspect ratio    : 16:9
Frame rate mode                  : Variable
Frame rate                       : 21.479 fps
Minimum frame rate               : 0.922 fps
Maximum frame rate               : 23.976 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.132
Stream size                      : 1.29 MiB (100%)
Writing library                  : x264 core 85 Ubuntu_2:0.85.1448+git1a6d32-3
Encoding settings                : cabac=1 / ref=4 / deblock=1:0:0 / analyse=0x3:0x113 / me=umh / subme=8 / psy=1 / psy_rd=1.00:0.00 / mixed_ref=1 / me_range=16 / chroma_me=1 / trellis=1 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=1 / chroma_qp_offset=-2 / threads=6 / sliced_threads=0 / nr=0 / decimate=1 / mbaff=0 / constrained_intra=0 / bframes=3 / b_pyramid=0 / b_adapt=2 / b_bias=0 / direct=3 / wpredb=1 / wpredp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc_lookahead=40 / rc=crf / mbtree=1 / crf=24.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / ip_ratio=1.41 / aq=1:1.00

```

Like I said I get the "Sorry, this video cannot be played." error when I try to launch it on my Nexus. The one difference I notice is the codec ID and the writing library are different. Don't know how to change this though.

---

### Post by littlepeon on 2010-04-02
hey original poster....

i do not have a nexus one so i cant test this.....

i was on another command line forum looking for mplayer tips/tricks and someone had posted this.....my question is will it work with your setup?


ffmpeg -i foobar.mpg -s 800x480 -vcodec mpeg4 -acodec libfaac -ac 2 -ar 16000 -r 13 -ab 32000 -aspect 16:9 foobar.mp4

---

### Post by StevieS on 2010-04-02
There's a lot of information about encoding for Android phones here,

[https://help.ubuntu.com/community/AndroidVideoEncoding](https://help.ubuntu.com/community/AndroidVideoEncoding)

I personally prefer using ffmpeg, the command line given works, but the Nexus One can handle much higher quality videos than the G1, so I edited the command line a bit to this instead

```
ffmpeg -i source-video.avi -vcodec mpeg4 -sameq -acodec libfaac -ac 1 -ar 16000 -ab 32000 output-video.mp4
```

The changes I made were

 - Add the -sameq flag to encode at the same quality as the original
 - Remove the -r 13 flag so that the original framerate is preserved
 - Remove the -s 480x320 flag, you may still need to resize your videos if they are very large
 - Change -acodec aac to -acodec libfaac as this command has changed
 - Remove the -aspect 3:2 to preserve the original aspect ratio

For me this produces a video which is just as high quality as the original and which plays perfectly on my Nexus One.

Let us know whether this works for you.

---

### Post by snares on 2010-04-06
Thanks for the help StevieS. Worked great but the audio is still ahead of the video. Any idea as to how to fix this?

---


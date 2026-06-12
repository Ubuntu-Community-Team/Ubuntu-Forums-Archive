---
title: "Converting avi files to smaller file size"
date: 2013-09-04
forum: Multimedia Software
---

### Post by Frdric_Lvesque on 2013-09-04
Hi!

My camera produces AVI files rather huge. I want to convert them to smaller files, for archiving. If I could go from 100Mo/min to about 6Mo/min that would be great. :) How can I do that? 

I use ubuntu 10.04 64 bits.

Thank you!

---

### Post by GwL3eNC on 2013-09-04
Hello,

avidemux is an application you can try.

sudo apt-get install avidemux 

I'm shure you can find an english side about it's functionality. If you have
no experience with video compression it's a bit learning for you. You can
get a smaller file if you choose a lower video bitrate and/or a lower audio
bitrate. A compression results always in lower quality. You have to play 
around with the video bitrate and video resolution to find your satisfiying result.

---

### Post by SeijiSensei on 2013-09-04
You have a couple of choices:

1)  Reduce the size of the video.  Because the size of a video file is proportional to the area of the image, reducing a 1920x1080 image to 1280x720 will result in a file that is only 43% as large as the original.  Most people with normal eyesight have little ability to discriminate between the two resolutions, especially if it is being viewed on an HDTV at normal living-room distances.  I'd suggest this as the long-run strategy.  Tell your camera to shoot at 720p rather than 1080p.

2)  Reduce the number of frames shot.  Most HDTV video these days is shot at just under 24 frames per second. If your camera is running at some higher rate, like 60 fps, you could tell it to shoot at a slower pace.  Unless you spend most of your time filming subjects in rapid motion like athletes or flying birds, you'll probably see little difference at 24 fps.  

As for converting existing AVI files, you might give mencoder a try (sudo apt-get install mencoder).  Though it's a little long in the tooth, mencoder was originally developed by the [mplayer crew]("http://www.mplayerhq.hu/design7/info.html") to work with AVI.  To rescale a 1080p video to 720p, you can use the command:

```
mencoder -o output.avi -oac copy -ovc lavc -lavopts vcodec=mpeg4 -vf scale=1280:720 /path/to/input.avi
```

This copies the audio track intact, but rescales the video to 1280x720 and encodes it with the mpeg4 codec.  Because the output file name ends in .avi, mencoder will use the AVI container format.  For testing purposes, you can add the parameter "-endpos 120" to the list, and mencoder will stop after the first two minutes of recoding.  If the results look good, remove the -endpos parameter to let it run for the full duration.

---

### Post by FakeOutdoorsman on 2013-09-04
You can also use ffmpeg:

[list=1]
[*]Get ffmpeg. 10.04 is showing its age, the ffmpeg in the repo is even older, and FFmpeg development is very active. Most simple thing to do is to download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds), but there is also a step-by-step non-intrusive [guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) if you prefer.
[*]Then encode:
```
ffmpeg -i input -codec:v libx264 -preset medium -crf 23 -codec:a aac -strict experimental -b:a 192k -metadata title="A movie by Frdric_Lvesque" output.mp4
```
[/list]

You can tweak preset and crf for video encoding speed and quality. -b:a is audio bitrate (this encoder, aac, requires "-strict experimental"). See the [FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide) and [FFmpeg and AAC Encoding Guide](https://trac.ffmpeg.org/wiki/AACEncodingGuide) for detailed instructions.

---

### Post by Frdric_Lvesque on 2013-09-04
> **SeijiSensei said:**
> You have a couple of choices:

 1)  Reduce the size of the video.  

 2)  Reduce the number of frames shot.  


I guess there is a command line to show these info?

---

### Post by SeijiSensei on 2013-09-04
If you install mplayer and play the file from the command line, mplayer will report the information.

```

$ mplayer /path/to/some/video.avi

```

You'll see a result like this:

```

Playing XXXXXX.avi.
Detected file format: AVI format (libavformat)
[lavf] stream 0: video (mpeg4), -vid 0
[lavf] stream 1: audio (mp3), -aid 0
VIDEO:  [MP4V]  640x360  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in .
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 4 threads if supported.
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 128.0 kbit/4.17% (ratio: 16000->384000)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)

```

(I've removed a couple of irrelevant errors like the failed probe for an NVIDIA card.)  This file contains a video in 640x360 at 24 frames per second (actually 23.976 for reasons not worth going into here).  The video is encoded with mpeg4 and the audio with mp3.

If you use the excellent GUI front-end for mplayer, called SMPlayer, you can use Ctrl-I to pop up a box with the information about the current video.  Installing SMPlayer with "sudo apt-get install smplayer" will automatically install mplayer as well if it is not already on your system.

---

### Post by Yellow Pasque on 2013-09-04
> I guess there is a command line to show these info? 

```
sudo apt-get install mediainfo
mediainfo <filename>
```

EDIT: Nvm, mediainfo is not in Lucid repo.

---

### Post by Frdric_Lvesque on 2013-09-04
Thank you everyone, I think I can now move on following your excellent advices.

---

### Post by andrew.46 on 2013-09-05
> **SeijiSensei said:**
> If you install mplayer  [...]

Interestingly enough the MPlayer source (from svn) contains a little script in TOOLS/ called midentify.sh which helps identify a few aspects of a video and lines things up so a script can more easily extract information. For example:

```

andrew@skamandros~/media/videos$**[COLOR="#FF0000"] midentify.sh Decay_2012_1080p_HQ.avi [/COLOR]**
ID_VIDEO_ID=0
ID_AUDIO_ID=1
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=Lavf54.50.102
ID_CLIP_INFO_N=1
ID_FILENAME=Decay_2012_1080p_HQ.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=2739016
ID_VIDEO_WIDTH=1920
ID_VIDEO_HEIGHT=960
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=123496
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_START_TIME=0.00
ID_LENGTH=4566.98
ID_SEEKABLE=1
ID_CHAPTERS=0
ID_VIDEO_CODEC=ffodivx
ID_AUDIO_BITRATE=32000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
ID_AUDIO_CODEC=mpg123
ID_EXIT=EOF
andrew@skamandros~/media/videos$ 

```

Lots of other goodies in there as well...

---

### Post by SeijiSensei on 2013-09-05
Ah, I wondered where that was in Ubuntu.  I recall using midentify some years back on a non-Ubuntu system where it didn't carry the .sh extension.

A quick "locate midentify" shows the script is shipped as /usr/share/mplayer/midentify.sh.

---


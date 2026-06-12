---
title: "Old script for ffmpeg"
date: 2016-04-13
forum: Multimedia Software
---

### Post by GettingNowhere on 2016-04-13
Hi all.

I have a lot of mkv files that I wish to convert to mp4.  I use ff multi converter and put my files in the window and let it do its thing.
If I have one file, it takes about 2 hours to convert.
If I have 2 files (each the same size as the first), it should take 4 hours.  It takes a day and a half.
I thought about going the command line way, but don't know any of the "options" to put in.

I then found this old script called ffbc.sh from a previous thread:
[http://ubuntuforums.org/showthread.php?t=2017284](http://ubuntuforums.org/showthread.php?t=2017284)

It closed in 2013, and although there is a link to a "newer" script, the page is long gone.

I wonder if there is anyone out there who knows enough about ffmpeg and bash who could update it as I wouldn't have a clue.

I get the error:
```
WORKING MODE mp4
Your ffmpeg verson is version N-79139-gde1a0d4 Copyright (c) 2000-2016 the FFmpeg developers
configuration: --extra-libs=-ldl --prefix=/opt/--mandir=/usr/share/man --enable-avresample --disable-debug --enable-nonfree --enable-gpl --enable-version3 --enable-libopencore-amrnb --enable-libopencore-amrwb --disable-decoder=amrnb --disable-decoder=amrwb --enable-libpulse --enable-libfreetype --enable-gnutls --enable-libx264 --enable-libx265 --enable-libfdk-aac --enable-libvorbis --enable-libmp3lame --enable-libopus --enable-libvpx --enable-libspeex --enable-libass --enable-avisynth --enable-libsoxr --enable-libxvid --enable-libvidstab
Check mp4 container format ... OK
Check mkv container format ... OK
Check fAAC Audio Encoder ... NOK

```

I presume the last line means Not OK, as it then exits.

Ubuntu 14.04
FF Multi Converter 1.7.2

Thanks for looking.

---

### Post by deadflowr on 2016-04-13
Moved to the **Multimedia Software** sub-forum

---

### Post by coldraven on 2016-04-13
I did the following search in DuckDuckGo
[https://duckduckgo.com/?q=handbrake+mkv+to+mp4&t=canonical&ia=qa&iax=1](https://duckduckgo.com/?q=handbrake+mkv+to+mp4&t=canonical&ia=qa&iax=1)

What I got was this
>  First of all, ask yourself: Do you need to re-encode? If you only want to change the container from **MKV** **to** **MP4**, you don't need to encode anything, you just change the "wrapping" around the video. This doesn't lose **quality**. 
     You can swap containers easily with [FFmpeg ]("http://ffmpeg.org/")– you just have to tell it to copy the video and audio bitstreams: 
      ffmpeg -i input.mkv -c:v copy -c:a copy output.mp4
      There are also tools like [MP4Box ]("http://www.videohelp.com/tools/mp4box")which can create **MP4** media — the same exists for **MKV** with [MKVtoolnix ]("http://www.bunkus.org/videotools/mkvtoolnix/"). 
     Finally, learn the [difference between video codecs and containers ]("http://superuser.com/a/300997/48078"). This will help you understand why changing containers works and why **MP4** and **MKV** have little to do with video, actually. If you want to know more about FFmpeg – I wrote [a blog entry on the Super User blog ]("http://blog.superuser.com/2012/02/24/ffmpeg-the-ultimate-video-and-audio-manipulation-tool/")about it. 



So that should be easy and almost instant!

Edit: Sorry if that sounds flippant because I'm learning about this subject at the same time. Believe me, this is a field in which I am definitely not an expert.

---

### Post by goofprog on 2016-04-13
I know how to answer that.
1.  Check that ffmpeg was compiled with all the goodies with it.  I noticed that I had a bad quality mp4 from one session because it did not have H.264 compiled in.  I actually use the windows compiled one with wine and it works just fine.
2.  I do not know enough bash or even ffmpeg to be an expert but I use my own little script for converting AVI containers that have mpeg4 and mp3 to H.264 and AAC with a little scaling down to 360 pixels.

Here is an example that takes all the *.avi files and converts them to MP4 with 22000Hz and 128kbps sound at a scale down to 360 pixels.  The new file name has to be changed because the extended name of -phone.mp4 at the end just means it was resized for the purpose of playing on my new android.
[B]
find -name "*.avi" -exec wine ffmpeg -i {} -ar 22000 -ab 128k {}-phone.mp4 \;
[/B]
Does that help?  I guess I went too deep into the information.

---

### Post by GettingNowhere on 2016-04-14
Hi.
The container idea is in the original shell file - it checks to see if it's compatible with that route.
Unfortunately, a large amount are not.  It may be something to do with H.264 as was suggested.
I have checked and have everything up to date - according to apt.

Still doesn't work.
It's an audio encoder or decoder that is not O.K. but it seems to be the correct one.

Going to windows seems to be a step back.

Oh well, it was worth a try...

---

### Post by vasa1 on 2016-04-14
> **GettingNowhere said:**
> ...
Going to windows seems to be a step back.
+1

> **GettingNowhere said:**
> ...
Oh well, it was worth a try...
If you're patient and bump this thread occasionally, you'll definitely get the help you need. There are people here who know quite a bit. And they'll surely help!

---

### Post by FakeOutdoorsman on 2016-04-14
Why do you need MP4 in the first place? Is the output for a specific device?

I didn't look at the old script, but it seems like you want to re-mux ([stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy)) compatible streams from MKV to MP4, and re-encode those that are not compatible (typically anything that is not H.264 video and AAC audio). If this is what you want to do then you use ffprobe to check the formats then use an if/then statements in bash to either re-mux or re-encode each stream.

Using ffprobe to output video stream format:
```
$ ffprobe -loglevel error -select_streams v:0 -show_entries stream=codec_name -of default=nw=1 input.mkv
codec_name=h264
```
For audio:
```
$ ffprobe -loglevel error -select_streams a:0 -show_entries stream=codec_name -of default=nw=1 input.mkv
codec_name=aac
```

If you use "default=nw=1:nk=1" instead then ffprobe will omit the codec_name key in the output if you prefer.

Then use ffmpeg. Either remux:
```
ffmpeg -i input.mkv -map 0:v:0 -map 0:a:0 -c copy output.mp4
```
or re-encode:
```
ffmpeg -i input.mkv -map 0:v:0 -map 0:a:0 -c:v libx264 -c:a aac output.mp4
```
or do both depending on the input:
```
ffmpeg -i input.mkv -map 0:v:0 -map 0:a:0 -c:v copy -c:a aac output.mp4
```

MKV files can contain multiple video and audio streams, so I used the map option to choose the first video and first audio streams because that is what I told ffprobe to check. You can remove them if you prefer to use the [default stream selection](http://ffmpeg.org/ffmpeg.html#Stream-selection) behavior instead.

Stuff to consider:
[list]
[*]Add "-movflags +faststart" if you plan on viewing any of the videos via progressive download such as if you host the video on your own web site. Without it playback can only begin once the whole file is downloaded. Or add it anyway regardless...doesn't hurt anything.
[*]Add "-pix_fmt yuv420p" if the video is to be re-encoded. This is to ensure compatible "chroma subsampling"; otherwise dumb players may not be able to play the output.
[*]If the encoding is too slow add "-preset" and use a faster preset. Default is "medium". See [FFmpeg Wiki: H.264](https://trac.ffmpeg.org/wiki/Encode/H.264).
[*]It is recommended to use a recent ffmpeg when possible, but there is no reason to use Wine or a Windows build of ffmpeg. You can [compile ffmpeg yourself](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu), use [mc3man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) (for 14.04 users), upgrade your Ubuntu, or the easiest method is to simply [download an already compiled binary of ffmpeg for Linux](http://johnvansickle.com/ffmpeg/) and point your script to it.
[/list]

---

### Post by mc4man on 2016-04-14
Just to note about FF Multi Converter, - while it still seems to be developed the presets are outdated & for aac uses libfaac thru ffmpeg.
That's not going to be available in Ubuntu/Debian proper ever & reasonably unlikely via a ppa though it would be easy to do so. 
(-  I could  as improper licensing in ppa's doesn't seem to come up but still a  concern for little apparent gain. 

A front end that looks interesting (though never used) is hybrid - 
[http://www.selur.de/](http://www.selur.de/)
ppa - [https://launchpad.net/~djcj/+archive/ubuntu/hybrid](https://launchpad.net/~djcj/+archive/ubuntu/hybrid)

---

### Post by GettingNowhere on 2016-04-14
Well, actually, Fake Outdoorsman answered it - sort of.
in his code, he mentioned:
-c:a aac

That was the answer.
I just changed lines 125 & 129 from libfaac to aac, and it's working like a charm.

I will go through the full installation as suggested, but it works!
Thanks

---


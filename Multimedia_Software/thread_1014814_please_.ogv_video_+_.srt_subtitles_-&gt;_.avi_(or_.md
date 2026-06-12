---
title: "please: .ogv video + .srt subtitles -&gt; .avi (or similar)"
date: 2008-12-18
forum: Multimedia Software
---

### Post by JC Cheloven on 2008-12-18
Hi, I didin't care so far to cope with video, so please consider me as a newbie in this field.

The particular task I want to accomplish is to convert the [Stephen Fry video at the FSF]("http://www.gnu.org/fry/"), which is in .ogv format, including spanish subtitles (which are given in a separate .srt subtitles file) in a format which could be read by my windoze friends. Some of them may see the light... :-)

The target format could be .avi or anything else they can play easily. I don't want to ask them to install vlc, I'd rather to make sure they watch the video.

I was able to play it at 1) totem, and also at  2) vlc and 3) mplayer. 
In every case with some issue in the subtitles, be 1) the size of subtitles, be 2) missing subtitles for a while, be 3) an encoding iso vs. utf issue.

I tried to save/convert from vlc, but no success ("failed to open file" message). 

I don't care very much about the issues with subtitles, my main question is how to convert to avi or such. I'm struggling with it for the third day. I'ts time to ask the community ;-)

---

### Post by eye208 on 2008-12-18
There are very few formats that Windows can play out of the box. One of them is MPEG-1:
```
mencoder -mc 0 -noskip -vf harddup -ovc lavc -oac lavc -of lavf -lavcopts vcodec=mpeg1video:acodec=mp2 -lavfopts format=mpg -sub subtitles.srt -o outfile.mpg infile.ogv
```

Check out the -sub* options in the MEncoder manual page on how to change subtitles size, character encoding etc.

---

### Post by JC Cheloven on 2008-12-23
Thanks for your help, Eye. I ran mencoder the way you told me:

```
 mencoder -mc 0 -noskip -vf harddup -ovc lavc -oac lavc -of lavf -lavcopts vcodec=mpeg1video:acodec=mp2 -lavfopts format=mpg -sub fry2.srt -o fry2.mpg fry2.ogv
```

But I get an error about bitrate 224 being not allowed in mp2. Here is the output:

```
MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x7c00dd
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg stream 3 is of an unknown type
Ogg stream 4 is of an unknown type
Ogg file format detected.
VIDEO:  [theo]  300x168  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:300x168  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 24.0 kbit/6.80% (ratio: 3000->44100)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
SUB: Detected subtitle file format: subviewer
SUB: Read 93 subtitles.
SUB: Adjusted 1 subtitle(s).
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x88443f0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 300 x 168 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (300x168 fourcc=3167706d [mpg1])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
[mp2 @ 0x88443f0]bitrate 224 is not allowed in mp2
Couldn't open codec mp2, br=224.

Exiting...

```

As I've been unable to cope with this, I tried a different approach given that I'm more skilled with audio: I have recorded the translation of Stephen Fry's speech using my own voice, with the idea of replacing the soundtrack of the movie using any video editor at a later time. **The new soundtrack is ready**, but (to my surprise), changing the soundtrack in the movie is not as easy as I thought. I tried avidemux, kino, iriverter, pitivi, ogmrip, gtranscode ... but didn't find my way around. Many of these don't even read ogv format :-(

After a week on it, I start to be despaired. I'd like to send this piece of free software advice with my Christmas greetings to my friends, but no avail so far. So please, either solution would be welcome:

- fixing the issue with mencoder, to get a mpeg w/subtitles.
- replacing the soundtrack of the movie using a video editor.

Thanks.

---

### Post by shirilover on 2008-12-23
You can replace the audio stream using Avidemux.
After opening the video, go to Audio->Main Track and select from the Audio source drop-down(External AC3,MP3 or WAV). Then browse to select the new audio stream you wish to use.

Assuming the file actually opens in Avidemux, you can choose the output video codec on the left from the Video drop-down list(i.e. MPEG4 ASP Xvid4). You can then configure the settings for the video stream using the configure button. 
To add .srt subtitles to the video, click the Filters button. Select subtitles from the list at the left, choose subtitles (.sub, .srt) in the middle and click the '+' at the bottom. Browse to the .srt file you wish to add and select the font family, size and color you wish to use, then click OK until your filter is shown in the rightmost column.

Lastly, save your new file and wait for the encode to finish.

---

### Post by JC Cheloven on 2008-12-23
> **shirilover said:**
> You can replace the audio stream using Avidemux.
After opening the video, go to Audio->Main Track and select from the Audio source drop-down(External AC3,MP3 or WAV). Then browse to select the new audio stream you wish to use.

Assuming the file actually opens in Avidemux, ... ... ...

Thanks a lot shirilover. Avidemux was one of my first trials, but it doesn't read the video file. Running it from console, I can see this output:

```
5367674f -> 5367674f
  Ogg file detected..
First packet : not a header 66?
```

I've seen at 
[http://www.avidemux.org/admWiki/index.php?title=Input_formats](http://www.avidemux.org/admWiki/index.php?title=Input_formats)
that ogm is supported, but nothing is said about ogv. Perhaps this is the reason. 

Anyway, the info about avidemux being able to do so many things, is useful to me. I'll focus my efforts in finding an auxiliar tool able to transcode the original video to a format that avidemux can read, and I'll do the rest inside avidemux. I'll come back with my progress, if any.

---

### Post by JC Cheloven on 2008-12-24
Well, at the beginning I expected it to be easy, but has been a nightmare. 

-> I finally managed to convert the ogv video to mpeg. Used ffmpeg in command line for that purpose (no succes with the winff gui). Some understandable loss of quality, but ok otherwise.

-> I tried to use avidemux on the mpeg file to either stamp the subtitles or replace the soundtrack. The subtitles weren't even loaded, and the replaced soundtrack was very very choppy. Not to blame avidemux: It was probably my lack of knowledge. But it should be a bit easier anyway.

-> I ended up booting from my "odd partition", which has been unused for months, and ... well opening that default application that can be used to create a .wmv file easily.

I usually give "my linux newbies" the advice of not suddenly delete the OS they are used to, as they may need it for some particular purpose. But I thought that it wouldn't apply to me anymore. I was wrong :-( 

Happy days

---


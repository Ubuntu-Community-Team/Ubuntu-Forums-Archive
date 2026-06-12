---
title: "Converting a big VRO file, editing it, and trying to post it on youtube."
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by dogofthecourt on 2008-04-02
Hello,

I am a complete beginner to Ubuntu and Linux, so you will have to forgive me if this was covered elsewhere.  I've read many posts, but I'm still confused.

I have two extremely big VRO files from a DVD Camcorer.  I want to reduce the size of each and cut each file down to 10 minute clips that I can post on youtube.

The video editors I found don't seem to be working for me.  I converted the files to .ogg and made them smaller, but not shorter.

I need idiot proof instructions for downloading and installing a good program (I've heard nice things about Cinerella).

I am using a System 76 Gazelle with an Intel Core 2 Duo - I'm not sure if that matters.
Thanks.

Bill

---

### Post by warp99 on 2008-04-03
If you already have the quality and size of the video you want just use ffmpeg to cut the video down to 10 minute sections by using the time (-t) and start position (-ss) parameters

```
ffmpeg -i input.ogg -acodec copy -vcodec copy -t 00:10:00 output.ogg
```

then the next file -ss and -t :

```
ffmpeg -i input.ogg -acodec copy -vcodec copy -ss 00:10:00 -t 00:10:00 output2.ogg
```

then change the -ss position:

```
ffmpeg -i input.ogg -acodec copy -vcodec copy -ss 00:20:00 -t 00:10:00 output3.ogg
```

Very fast without having to install any video editing software.

---

### Post by dogofthecourt on 2008-04-03
Thanks.  That would probably work, except for the fact that I get this message:

"Usually that means that input file is truncated and/or corrupted." atb the end of the error message.

That may be beyond this forum.  I will say that the file plays perfectly on the computer, so I am not sure what the deal is.

---

### Post by dogofthecourt on 2008-04-03
Actually, I figured out that the problem above was that I had the wrong line to the directory.
Now, I get this however.
Any suggestions?

Input #0, mpeg, from 'VR_MOVIE.VRO':
  Duration: 00:03:58.1, start: 0.255589, bitrate: 47516 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 704x480, 9558 kb/s, 29.97 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, 256 kb/s
Unable for find a suitable output format for 'VR_MOVIE1.VRO'

I am using this line:

ffmpeg -i VR_MOVIE.VRO -acodec copy -vcodec copy -t 00:10:00 VR_MOVIE1.VRO


Any ideas?
I tried it with my ogg converted files and ran into problems as well.  I might try that again. however.

---

### Post by dogofthecourt on 2008-04-03
> **warp99 said:**
> If you already have the quality and size of the video you want just use ffmpeg to cut the video down to 10 minute sections by using the time (-t) and start position (-ss) parameters

```
ffmpeg -i input.ogg -acodec copy -vcodec copy -t 00:10:00 output.ogg
```

then the next file -ss and -t :

```
ffmpeg -i input.ogg -acodec copy -vcodec copy -ss 00:10:00 -t 00:10:00 output2.ogg
```

then change the -ss position:

```
ffmpeg -i input.ogg -acodec copy -vcodec copy -ss 00:20:00 -t 00:10:00 output3.ogg
```

Very fast without having to install any video editing software.


Now, it is working, but it tells me I need an Octet Stream decoder in MPlayer.  What do you think that means?

Thanks.

---

### Post by warp99 on 2008-04-04
If I'm not mistaken VRO files are just mpeg files. If you type the following:

```
ffmpeg -i VR_MOVIE.VRO 
```

ffmpeg will tell you the exact video and audio codecs being used. Now ffmpeg does not care about the input file extension, but the output extension determines the header information so try this string first:

```
ffmpeg -i VR_MOVIE.VRO -acodec copy -vcodec copy -t 00:10:00 VR_MOVIE1.mpg
```  

If that does not work you can encode the file while making the 10 minute sections to a format mplayer will be able to read:

```
ffmpeg -i VR_MOVIE.VRO -acodec ac3 -vcodec mpeg2video -sameq -t 00:10:00 VR_MOVIE.mpg

```

and you can make the file smaller if you want::

```
ffmpeg -i VR_MOVIE.VRO -acodec ac3 -vcodec mpeg2video -sameq -t 00:10:00 -s 320x240 VR_MOVIE.mpg
```

or reduce the quality :

```
ffmpeg -i VR_MOVIE.VRO -acodec ac3 -ar 48000 -ab 64k -vcodec mpeg2video -b 200k -t 00:10:00 VR_MOVIE.mpg
```

or do all three at the same time. Type 'man ffmpeg' for the available options.

---

### Post by dogofthecourt on 2008-04-04
It seems to be working now.
Thanks buddy.
Would you mind another question?
Is there a simple way to reduce the total size of the file?
Right now my 5 minute clip is over 300 mb.  I need it at 100mb.

I'm trying

ffmpeg VR_MOVIE1.mpg -fs 100 iceland1.mpg

right now.

---

### Post by warp99 on 2008-04-04
Use the last string of the previous post with some changes:

```
ffmpeg -i VR_MOVIE.VRO -acodec ac3 -ar 48000 -ab 128k -vcodec mpeg2video -b 750k -t 00:10:00 VR_MOVIE.mpg
```

You may have to change the video bitrate (-b 750k) to something higher for better quality since you original file had a bitrate of over **9,000 kb/s **, but anything over 3000kb/s is overkill. With youtube flash video 750kb/s is most likely overkill, but it's a starting point and you can always move the rate down for a smaller file.

---

### Post by dogofthecourt on 2008-04-04
I decided to go with 5 minute clips.  The first one came out fine - thanks again.
I converted it with an ogg converter to get it down in size before I read your recent post.
I am having problems with editing out the second 5 minute clip.
Do you have any thoughts?  Thanks again.

ffmpeg -i VR_MOVIE.VRO -acodec ac3 -vcodec mpeg2video -sameq -ss 00:05:00 -t 00:05:00 VR_MOVIE2.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:22:28, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from 'VR_MOVIE.VRO':
  Duration: 00:03:58.1, start: 0.255589, bitrate: 47516 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 704x480, 9558 kb/s, 29.97 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, 256 kb/s
Output #0, mpeg, to 'VR_MOVIE2.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 704x480, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
No accelerated IMDCT transform found
Press [q] to stop encoding
frame=    0 q=0.0 Lsize=       0kB time=10000000000.0 bitrate=   0.0kbits/s    
video:0kB audio:0kB global headers:0kB muxing overhead nan%

---

### Post by warp99 on 2008-04-04
You mean "No accelerated IMDCT transform found" that's just normal output. As for the next video you can just use the copy command:

```
ffmpeg -i VR_MOVIE.VRO -acodec copy -vcodec copy -ss 00:05:00 -t 00:05:00 VR_MOVIE2.mpg
```

It has something to do with the time stamp with some file formats, usually it's the index on .avi files. Just use the copy command, then re-encode later at a lower bit rate to shrink the file size.

Recently I found an extensive guide about all of the commands available with ffmpeg:

[http://www.itbroadcastanddigitalcinema.com/ffmpeg_howto.html](http://www.itbroadcastanddigitalcinema.com/ffmpeg_howto.html)

Edit:

According to the guide for mpeg-2 video you may need to use the MPEG-2 -timecode_frame_start parameter

> Note : Start timecode is set as number of frames. For instance, if you want to start at 18:12:36:15, you will have to set -timecode_frame_start to 1638915 ( for 25 fps content ).

So if you know the fps (29.97 fps) for your video then (00:05:00 x 60) * 29.97 would start at 8991

---

### Post by dogofthecourt on 2008-04-05
I can't tell you how much I appreciate your help.
I got the first five minutes of my Iceland video up at 
[http://www.youtube.com/watch?v=dMWgg3SSLpc](http://www.youtube.com/watch?v=dMWgg3SSLpc)

I'm glad that I got a linux system because I enjoy the challenge and people are willing to help.
I tried to do it with a start of 9000 which would be 5minutes in on a 30fps speed - which the player tells me that I have.  It didn't work as the new file started at the beginning.

 ffmpeg -i VR_MOVIE.VRO -acodec copy -vcodec copy -timecode_frame_start 9000 -t 00:05:00 VR_MOVIE2.mpg

I've played around with different things and looked at guides, but still I am confused.
Would you mind helping me again?

Thanks.

Bill

---

### Post by dogofthecourt on 2008-04-05
I seem to be having better luck with Avidemux and the ogg converter at this point.
Almost have part 2 up.
Thanks.

---

### Post by warp99 on 2008-04-05
Avidemux is good since it's a GUI front end for mencoder, which is a command line utility similar to ffmpeg. Mencoder on the command line is very difficult to use so I'm glad that you having good results with Avidemux. Sometimes with different types of video mencoder will work better then ffmpeg and with others it's the opposite, so it all depends. On your next video project I would keep both programs in the toolbox so to speak.

BTW the video of your trip looks good. Noticed a lot of new construction on the island, Icelanders must be doing well.

---


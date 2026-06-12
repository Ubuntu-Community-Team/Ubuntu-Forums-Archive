---
title: "Recording videos, Four problems"
date: 2010-06-03
forum: Multimedia Software
---

### Post by irv on 2010-06-03
I am going to cover these four problems in this thread. 
1.)Using gtk-recordMyDesktop and xvidcap for recording videos
2.)Saving files in ogv format
3.)Converting ogv to avi or wmv or ?
4.)Uploading ogv video to youtube

First, I am using Ubuntu 10.04 and have installed gtk-recordMyDesktop and it works great. Save a nice clear video with good sound. I can play it right from my system and also from my server but I can not upload it to youtube. Maybe I should say I can't upload a good video to youtube. It uploads OK but it is un-viewable. Just to make sure it wasn't a Ubuntu problem I tried uploading it from Windows 7. Same thing.
The next thing I tried was to convert it to another file format and even before I uploaded it, it was un-viewable. (looked the same as when it was uploaded to youtube). I tried the conversion in a Windows program called AVS and I also tried doing it with VLC in Ubuntu. VLC just give me a blank file after converting. 
I don't think the problem is with youtube but with the file itself. 
To be honest with you I believe the video is high quality but I don't see how I can put them on youtube.
Has anyone converted ogv files to another format which looks good and can be uploaded to youtube?
Has anyone uploaded a ogv file to youtube and have it look good?
Does anyone know anything I can try to get a good viewable file up to youtube.
I tried recording a video with xvidcap and get a good video and it looks good on youtube but I can't get the sound to work with it. All I get is clicking in the video. File is in mpeg format. 

Here is a youtub video to show you the un-viewable video.
[http://www.youtube.com/watch?v=AhKf1swwcFU]("http://www.youtube.com/watch?v=AhKf1swwcFU")

---

### Post by lovinglinux on 2010-06-03
RecordMyDesktop is totally screwed in Lucid. I don't know if it is a ogv problem or the application itself. Here I can't even watch the recorded video, it looks like your Youtube video. Additionally, sometimes it adds several minutes of a static desktop image to the recorded video.

The solution for me is to convert the ogv with mencoder. Then it can be viewed locally and uploaded to YouTube.

Here is the command I use to convert the video:

```
mencoder source.ogv  -o output.avi -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

---

### Post by irv on 2010-06-03
> **lovinglinux said:**
> RecordMyDesktop is totally screwed in Lucid. I don't know if it is a ogv problem or the application itself. Here I can't even watch the recorded video, it looks like your Youtube video. Additionally, sometimes it adds several minutes of a static desktop image to the recorded video.

The solution for me is to convert the ogv with mencoder. Then it can be viewed locally and uploaded to YouTube.

Here is the command I use to convert the video:

```
mencoder source.ogv  -o output.avi -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

Thanks for the tip, I ran the code and it works and converted the ogv to the avi file and the video runs but without sound. It looks like it converts the video part of the file but does not bring the sound over to be part of the avi file.

---

### Post by lovinglinux on 2010-06-03
> **irv said:**
> Thanks for the tip, I ran the code and it works and converted the ogv to the avi file and the video runs but without sound. It looks like it converts the video part of the file but does not bring the sound over to be part of the avi file.

Oh sorry. Most videos I record have no sound and I add sound with YouTube audio swap.

Try another audio codec like this:

```
mencoder source.ogv -o output.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

---

### Post by irv on 2010-06-03
I forgot to include the output of the code I ran in the above post:
> irv@irv-laptop:~$ mencoder How-I-Update-My-Server.ogv  -o How-I-Update-My-Server.avi -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x1700cda
Ogg stream 0 is of an unknown type
[Ogg] stream 1: video (Theora v3.2.1), -vid 0
[Ogg] stream 2: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  1280x800  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1280x800  fps:15.000  ftime:=0.0667
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 1 ch, s16le, 90.0 kbit/25.51% (ratio: 11248->44100)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x97e7a80]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1280 x 800 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.60:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1280x800 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   1.5s     22f ( 1%)  0.00fps Trem:   0min  21mb  A-V:0.138 [1959:38]
Skipping frame!
Pos: 153.7s   2306f (99%) 44.18fps Trem:   0min  17mb  A-V:0.050 [902:37]]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  902.880 kbit/s  (112859 B/s)  size: 17342812 bytes  153.667 secs  2306 frames

Audio stream:   37.983 kbit/s  (4747 B/s)  size: 725849 bytes  152.880 secs
irv@irv-laptop:~$ 


---

### Post by irv on 2010-06-03
> **lovinglinux said:**
> Oh sorry. Most videos I record have no sound and I add sound with YouTube audio swap.

Try another audio codec like this:

```
mencoder source.ogv -o output.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

I gave the last codec you gave me and it worked like a champ. 
Thanks again. This is some good stuff. I am going to try to upload it to youtube and I will post a link to it when it is out there.

addition: here is the link to the uploaded video on youtube. It worked very well. Thanks again for all your help.
[http://www.youtube.com/watch?v=mKcv81rkMAQ]("http://www.youtube.com/watch?v=mKcv81rkMAQ")

---

### Post by lovinglinux on 2010-06-03
> **irv said:**
> I gave the last codec you gave me and it worked like a champ. 
Thanks again. This is some good stuff. I am going to try to upload it to youtube and I will post a link to it when it is out there.

You are welcome.

---

### Post by irv on 2010-06-04
Just for the record: the ogv file that is generated from the application "Cheese" will not upload to youtube. It seems like any ogv file will not upload so you have to convert them it avi or mpeg etc.
Has other versions of Ubuntu had this problem or is this something new in 10.04?

---

### Post by lovinglinux on 2010-06-04
> **irv said:**
> Just for the record: the ogv file that is generated from the application "Cheese" will not upload to youtube. It seems like any ogv file will not upload so you have to convert them it avi or mpeg etc.
Has other versions of Ubuntu had this problem or is this something new in 10.04?

I use Ubuntu since Hardy and this is the first time I see such problem.

---

### Post by irv on 2010-06-04
I been following the [http://ubuntuforums.org/showthread.php?t=1465548]("http://ubuntuforums.org/showthread.php?t=1465548") on this forum, and this release has been very buggy. 
I believe all the video and audio problems are because of missing or changes in file that are not working the way they should Take for example when running the ffmpeg to convert ogv to avi's I get this error and I have the Ubuntu extras on codesc's installed.

```
irv@irv-laptop:~/Desktop$ ffmpeg -i desktop_video.ogv destop_video.avi

FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.

  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static

  libavutil     49.15. 0 / 49.15. 0

  libavcodec    52.20. 1 / 52.20. 1

  libavformat   52.31. 0 / 52.31. 0

  libavdevice   52. 1. 0 / 52. 1. 0

  libavfilter    0. 4. 0 /  0. 4. 0

  libswscale     0. 7. 1 /  0. 7. 1

  libpostproc   51. 2. 0 / 51. 2. 0

  built on Mar  4 2010 12:35:30, gcc: 4.4.3

[ogg @ 0x8f6ba60]Could not find codec parameters (Invalid Codec type -1)

[ogg @ 0x8f6ba60]Could not find codec parameters (Video: theora, 1280x800)

Input #0, ogg, from 'desktop_video.ogv':

  Duration: 00:00:18.94, start: 0.000000, bitrate: 572 kb/s

    Stream #0.0: Invalid Codec type -1

    Stream #0.1: Video: theora, 1280x800, PAR 1:1 DAR 8:5, 15 tbr, 15 tbn, 15 tbc

    Stream #0.2: Audio: vorbis, 22050 Hz, mono, s16, 89 kb/s

swScaler: Unknown format is not supported as input pixel format

Cannot get resampling context

```

And here is the error I get if I try to run the converted video.
[ATTACH]159352[/ATTACH]

I have found workarounds but one should not have to do this. This is not good for us Ubuntu users. Sometimes I think we are moving to quickly trying to bring new things in the OS. Maybe we need to slow down and get what we have working before trying to do these upgrades.

---

### Post by irv on 2010-06-04
Now that I found this Application WinFF, I like how easy it is to convert video files.
[ATTACH]159364[/ATTACH]
But now I want to get rid of this error
[ATTACH]159365[/ATTACH]
when it runs, but I need a little help. From the screen shots can someone tell me what is causing this (Invalid Codec type -1)? I loaded the codec's.

---

### Post by lovinglinux on 2010-06-04
> **irv said:**
> Now that I found this Application WinFF, I like how easy it is to convert video files.
[ATTACH]159364[/ATTACH]
But now I want to get rid of this error
[ATTACH]159365[/ATTACH]
when it runs, but I need a little help. From the screen shots can someone tell me what is causing this (Invalid Codec type -1)? I loaded the codec's.

WinFF is not working for me. It doesn't load at all.

---

### Post by irv on 2010-06-04
> **lovinglinux said:**
> WinFF is not working for me. It doesn't load at all.

Looks like we both are having issues but different ones. Did you try to purge it and then re-install it?

---

### Post by lovinglinux on 2010-06-04
> **irv said:**
> Looks like we both are having issues but different ones. Did you try to purge it and then re-install it?

Yes. It hasn't been working for me since Karmic and I did a clean install of Lucid. I mostly use mencoder from command-line, so I'm not worried about WinFF.

---

### Post by irv on 2010-06-04
> **lovinglinux said:**
> Yes. It hasn't been working for me since Karmic and I did a clean install of Lucid. I mostly use mencoder from command-line, so I'm not worried about WinFF.

From the looks of the responses we are getting on this thread we both will be using mencoder. It does work, but I am one of these guys, if it broken fix it. If it not leave it alone.

---

### Post by irv on 2010-06-05
> **lovinglinux said:**
> WinFF is not working for me. It doesn't load at all.

I was determine not to give up. I got it to work.
I first  uninstall the x264, libx264, and the ffmpeg and reinstalled everything following the this howto:
 [http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

Then I reinstalled a few packages like VLC WinFF.

The first thing I did was to convert a ogv to a avi using WinFF.

I also tried this command and it worked:

```
irv@irv-laptop:~/ffmpeg$ ffmpeg -i /home/irv/Desktop/xxx.ogv /home/irv/Desktop/xxx3.avi
```

This was the output in the terminal 

> FFmpeg version SVN-r23493, Copyright (c) 2000-2010 the FFmpeg developers

  built on Jun  5 2010 13:26:38 with gcc 4.4.3

  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab

  libavutil     50.18. 0 / 50.18. 0

  libavcodec    52.74. 1 / 52.74. 1

  libavformat   52.68. 0 / 52.68. 0

  libavdevice   52. 2. 0 / 52. 2. 0

  libavfilter    1.20. 0 /  1.20. 0

  libswscale     0.11. 0 /  0.11. 0

  libpostproc   51. 2. 0 / 51. 2. 0

[theora @ 0xa2058c0]7 bits left in packet 82

Input #0, ogg, from '/home/irv/Desktop/xxx.ogv':

  Duration: 00:00:05.50, start: 0.000000, bitrate: 7295 kb/s

    Stream #0.0: Video: theora, yuv420p, 1600x1200, 10 tbr, 10 tbn, 10 tbc

    Stream #0.1: Audio: vorbis, 44100 Hz, mono, s16, 80 kb/s

[theora @ 0xa2058c0]7 bits left in packet 82

Output #0, avi, to '/home/irv/Desktop/xxx3.avi':

  Metadata:

    ISFT            : Lavf52.68.0

    Stream #0.0: Video: mpeg4, yuv420p, 1600x1200, q=2-31, 200 kb/s, 10 tbn, 10 tbc

    Stream #0.1: Audio: mp2, 44100 Hz, mono, s16, 64 kb/s

Stream mapping:

  Stream #0.0 -> #0.0

  Stream #0.1 -> #0.1

Press [q] to stop encoding

frame=   55 fps= 19 q=31.0 Lsize=     592kB time=4.83 bitrate=1004.3kbits/s    

video:539kB audio:38kB global headers:0kB muxing overhead 2.691980%

irv@irv-laptop:~/ffmpeg$ 

I did have to change the preferences in the WinFF. Here is a screen shot:
[ATTACH]159453[/ATTACH]
As you can see I have to change the path to the ffmpeg and the ffplay.
That's it, and now it works.

---

### Post by lovinglinux on 2010-06-05
> **irv said:**
> I was determine not to give up. I got it to work.
I first  uninstall the x264, libx264, and the ffmpeg and reinstalled everything following the this howto:
 [http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

Then I reinstalled a few packages like VLC WinFF.

The first thing I did was to convert a ogv to a avi using WinFF.

I also tried this command and it worked:

```
irv@irv-laptop:~/ffmpeg$ ffmpeg -i /home/irv/Desktop/xxx.ogv /home/irv/Desktop/xxx3.avi
```

This was the output in the terminal 



I did have to change the preferences in the WinFF. Here is a screen shot:
[ATTACH]159453[/ATTACH]
As you can see I have to change the path to the ffmpeg and the ffplay.
That's it, and now it works.

Thanks for sharing.

---

### Post by Guitar John on 2010-06-05
YouTube can play ogv.  At least it could in April.  I recorded a video with my flip Mino HD and edited it down with ffmpeg2theora.  Interesting side note is that the flip records in mp4.  I converted it to ogv and when I uploaded it to YouTube, it is re-encoded back to mp4 and flv.  

My reason for converting it was to test out the capabilities of ffmpeg2theora, as well as to see if YouTube would accept the format.

The results:
[http://www.youtube.com/watch?v=1D5jZJn7rsc](http://www.youtube.com/watch?v=1D5jZJn7rsc)

---

### Post by irv on 2010-06-06
> **Guitar John said:**
> YouTube can play ogv.  At least it could in April.  I recorded a video with my flip Mino HD and edited it down with ffmpeg2theora.  Interesting side note is that the flip records in mp4.  I converted it to ogv and when I uploaded it to YouTube, it is re-encoded back to mp4 and flv.  

My reason for converting it was to test out the capabilities of ffmpeg2theora, as well as to see if YouTube would accept the format.

The results:
[http://www.youtube.com/watch?v=1D5jZJn7rsc](http://www.youtube.com/watch?v=1D5jZJn7rsc)

Hey Guitar John, Are you sure youtube will play ogv files? I have tried uploading them about a 1/2 dozen times and have not got one to work. Here is what they look like:[ http://www.youtube.com/watch?v=AhKf1swwcFU]("http://www.youtube.com/watch?v=AhKf1swwcFU"). As we I write this I am running ffmpeg2throra on a ogv file and will try to upload it when it is done. I believe it will do the same thing as all the other I have uploaded.

Edit: it was the same: [http://www.youtube.com/watch?v=HvbaJQ4RvZQ]("http://www.youtube.com/watch?v=HvbaJQ4RvZQ")

---

### Post by Guitar John on 2010-06-06
In addition to the one that I linked, I uploaded four that were made using Cheese.  YouTube accepted all of them.  

[link]("http://www.youtube.com/watch?v=SsJpB8gZjo4")

But they were all made using Ubuntu 9.10 and I have upgraded to 10.04 since then.  I do not know if something changed with Lucid, that may be at the root of your problem.  Or it could be that something changed on YouTube's end since April.  

Either one of those could be the culprit.

EDIT: The quality of your "Video of my laptop" appears to be quite good, including the inset running Cheese.  Based on that, I am inclined to think that this problem may be on YouTube's end.  Perhaps something *has* changed since April.

---

### Post by irv on 2010-06-06
> **Guitar John said:**
> In addition to the one that I linked, I uploaded four that were made using Cheese.  YouTube accepted all of them.  

[link]("http://www.youtube.com/watch?v=SsJpB8gZjo4")

But they were all made using Ubuntu 9.10 and I have upgraded to 10.04 since then.  I do not know if something changed with Lucid, that may be at the root of your problem.  Or it could be that something changed on YouTube's end since April.  

Either one of those could be the culprit.

EDIT: The quality of your "Video of my laptop" appears to be quite good, including the inset running Cheese.  Based on that, I am inclined to think that this problem may be on YouTube's end.  Perhaps something *has* changed since April.

The videos you are referring to were uploaded as avi after I converted them. The one ogv in my signature is running off my server.

If anyone out here is running 9.04 or 9.1 could upload a ogv file to youtube this would tell us if the problem is with 10.04.

---

### Post by Guitar John on 2010-06-06
I just found this.

Someone else had the same issue, and posted a workaround on Youtube:
[http://www.youtube.com/watch?v=FO7_6CUh1M4](http://www.youtube.com/watch?v=FO7_6CUh1M4)

---

### Post by ron999 on 2010-06-06
Hi irv
I'm using Ubuntu 9.10 Karmic.
I downloaded the ogg video from your signature.
It played OK on my PC using mPlayer and VLC.:)
I've uploaded it to YouTube... and it looks terrible.:(
Here it is:-[http://www.youtube.com/watch?v=-lK196QdCeE]("http://www.youtube.com/watch?v=-lK196QdCeE")

---

### Post by irv on 2010-06-06
> **Guitar John said:**
> I just found this.

Someone else had the same issue, and posted a workaround on Youtube:
[http://www.youtube.com/watch?v=FO7_6CUh1M4](http://www.youtube.com/watch?v=FO7_6CUh1M4)

Thanks for the post, This work around works, but it still doesn't answer the question why ogv files no longer upload to youtube. I would still like to know if it youtube or 10.04 fault that they don't.

---

### Post by Guitar John on 2010-06-06
> **irv said:**
> Thanks for the post, This work around works, but it still doesn't answer the question why ogv files no longer upload to youtube. I would still like to know if it youtube or 10.04 fault that they don't.

From what I am reading [here]("http://www.google.com/support/forum/p/youtube/thread?tid=7b9148c46c6b6f90&hl=en"), 

> It seems that Ubuntu Lucid 10.04 updated to Theora 1.1 but YouTube didn't

So it would seem that the blame can be shared equally.

---


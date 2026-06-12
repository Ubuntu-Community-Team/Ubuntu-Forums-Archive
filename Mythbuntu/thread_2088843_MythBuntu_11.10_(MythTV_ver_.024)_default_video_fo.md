---
title: "MythBuntu 11.10 (MythTV ver .024) default video format"
date: 2012-11-27
forum: Mythbuntu
---

### Post by johnfm3 on 2012-11-27
I am seeking how to change the default recorded video format on mythtv?
 
With handbrake, most my movies are about 1.5GB for a 2hr movie.  MythTV records a 60 min video at 6GB.
 
I would like to make use of the H.264 format so my videos can be watched on my Roku without transcoding which tanks my CPU utilization on my Myth/Plex media server.
 
John

---

### Post by johnfm3 on 2012-11-27
Via CLI:  Any good suggestion finding out how to determin what video format a video file is?
 
John

---

### Post by tgm4883 on 2012-11-27
The video type is dependent on your tuner. If it's a digital tuner, then it's likely mpeg2 (and with that size/hr, it likely is mpeg2). The HDPVR is the only one I know of that records directly to h.264, for everything else, you'll need to transcode. You can set that up as a job for after recordings are done.

---

### Post by johnfm3 on 2012-11-27
> **tgm4883 said:**
> The video type is dependent on your tuner. If it's a digital tuner, then it's likely mpeg2 (and with that size/hr, it likely is mpeg2). The HDPVR is the only one I know of that records directly to h.264, for everything else, you'll need to transcode. You can set that up as a job for after recordings are done.
 
 
Based on your comments, I did some looking an found the following supported on some forums...
 
"Since it tunes only digital signals (OTA HDTV as well as "Clear" QAM digital cable), which are already MPEG2 encoded, it has no MPEG encoding hardware"
 
That being said.  You suggested I can setup a Job.  I know where the 4 job fields are.  Assuming thats what your talking about.  Do you have an example job I could try?  I have installed ffmpeg an mplayer2 already.  Unsure if it was needed.
 
Thanks,
John

---

### Post by tgm4883 on 2012-11-27
I don't transcode myself, so the best I can do is point you here

[http://www.mythtv.org/wiki/Transcode_cron_job](http://www.mythtv.org/wiki/Transcode_cron_job)

[http://www.mythtv.org/wiki/Mythtranscode](http://www.mythtv.org/wiki/Mythtranscode)

---

### Post by johnfm3 on 2012-11-27
> **tgm4883 said:**
> I don't transcode myself, so the best I can do is point you here
 
[http://www.mythtv.org/wiki/Transcode_cron_job](http://www.mythtv.org/wiki/Transcode_cron_job)
 
[http://www.mythtv.org/wiki/Mythtranscode](http://www.mythtv.org/wiki/Mythtranscode)
 
Hey, thanks.  The transcode cron job seems like a good solution.  I will look into whether I can add that to the jobs field so it can be ran after video creation.
 
Anyother thoughts anyone?
 
John

---

### Post by nickrout on 2012-11-27
> **johnfm3 said:**
> Hey, thanks.  The transcode cron job seems like a good solution.  I will look into whether I can add that to the jobs field so it can be ran after video creation.
 
Anyother thoughts anyone?
 
JohnYep, save yourself a lot of time and trouble and get a bigger hard drive. Transcoding to h.264 will tie up a lot of resources and take ages, for something you are probably going to watch and delete. It is also prone to error. Take a look at the mythtv-users mailing list and a good percentage of the posts are about people whose transcode jobs have failed.

---

### Post by johnfm3 on 2012-11-28
> **nickrout said:**
> Yep, save yourself a lot of time and trouble and get a bigger hard drive. Transcoding to h.264 will tie up a lot of resources and take ages, for something you are probably going to watch and delete. It is also prone to error. Take a look at the mythtv-users mailing list and a good percentage of the posts are about people whose transcode jobs have failed.
 
 
Thanks for your comment.  Saddly, thats not an option for me.  I have to many Roku's for my kids an the video cant play on them without the machine transcoding.  An that results in bogging down the machine even more.  I have 5 kids, an now 4 roku's.  When more than 1 of them trys to view a video where the machine needs to transcode (which is almost every video), the Myth Server crys.
 
I know I need a new machine with more HD, proc, an ram abilities.  But for the short term, I need to setup transcoding for these roku's that I am going to keep till I can upgrade to AppleTV.
 
Your post also makes me ask another question...
Can I transcode an save the video in another dir an leave the Original File in place till confirmation of successful conversion?
 
John

---

### Post by FakeOutdoorsman on 2012-11-28
> **johnfm3 said:**
> Via CLI:  Any good suggestion finding out how to determin what video format a video file is?
 
John

```
$ ffmpeg -i IronMan.mkv 
[...]
Input #0, matroska,webm, from 'IronMan.mkv':
  Metadata:
    creation_time   : 2008-10-22 06:43:30
  Duration: 00:01:48.50, start: 0.000000, bitrate: 4141 kb/s
    Stream #0:0: Video: h264 (High), yuv420p, 1280x720, SAR 115:87 DAR 1840:783, 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Stream #0:1: Audio: aac, 48000 Hz, stereo, fltp (default)
```

For more detailed information about the input try **ffprobe**.

---

### Post by johnfm3 on 2012-11-28
> **FakeOutdoorsman said:**
> ```
$ ffmpeg -i IronMan.mkv 
[...]
Input #0, matroska,webm, from 'IronMan.mkv':
  Metadata:
    creation_time   : 2008-10-22 06:43:30
  Duration: 00:01:48.50, start: 0.000000, bitrate: 4141 kb/s
    Stream #0:0: Video: h264 (High), yuv420p, 1280x720, SAR 115:87 DAR 1840:783, 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Stream #0:1: Audio: aac, 48000 Hz, stereo, fltp (default)
```
 
For more detailed information about the input try **ffprobe**.
 
Thanks.  Will try that when I get home.
 
John

---

### Post by nickrout on 2012-11-28
> **johnfm3 said:**
> Thanks for your comment.  Saddly, thats not an option for me.  I have to many Roku's for my kids an the video cant play on them without the machine transcoding.  An that results in bogging down the machine even more.  I have 5 kids, an now 4 roku's.  When more than 1 of them trys to view a video where the machine needs to transcode (which is almost every video), the Myth Server crys.
 
I know I need a new machine with more HD, proc, an ram abilities.  But for the short term, I need to setup transcoding for these roku's that I am going to keep till I can upgrade to AppleTV.
 
Your post also makes me ask another question...
Can I transcode an save the video in another dir an leave the Original File in place till confirmation of successful conversion?
 
JohnPerhaps you need to rethink your playback devices. Revos or other ION machines are quite cheap. Roku is not designed to work with mpeg2 video.

You can write any transcoding script you like, and it can write the transcoded file anywhere you like, and you can do anything you like with the old file.

---

### Post by johnfm3 on 2012-11-28
> **nickrout said:**
> Perhaps you need to rethink your playback devices. Revos or other ION machines are quite cheap. Roku is not designed to work with mpeg2 video.
 
You can write any transcoding script you like, and it can write the transcoded file anywhere you like, and you can do anything you like with the old file.
 
 
Upgrades are in the works....  But $$$$ is needed to do so.  So I need an alternative till funds allow for appleTV (@$100 each) to replace the roku's.
 
Since my experiance with media is minimal, I am still seeking example code as well as suggestions to accomplish my current goal.
 
Thanks,
John

---

### Post by nickrout on 2012-11-28
> **johnfm3 said:**
> Upgrades are in the works....  But $$$$ is needed to do so.  So I need an alternative till funds allow for appleTV (@$100 each) to replace the roku's.
 
Since my experiance with media is minimal, I am still seeking example code as well as suggestions to accomplish my current goal.
 
Thanks,
JohnJoin mythtv-users, there are plenty of people working on transcoding there.

Best way to detect video codecs etc is mediainfo.

Not sure appleTV is the right answer either, I don't think mythfrontend runs on it.

I recently built a frontend for about NZ$150 (compaq sff dc7100 $50, Asus GT520 half height fanless card $80, remote $20) - our IT stuff tends to be twice the US$ amount so you could probably build a proper frontend for $70-80 US$.

Not small, but works well and sits in the TV stand quite well.

---

### Post by johnfm3 on 2012-11-28
> **nickrout said:**
> Join mythtv-users, there are plenty of people working on transcoding there.
 
Best way to detect video codecs etc is mediainfo.
 
Not sure appleTV is the right answer either, I don't think mythfrontend runs on it.
 
I recently built a frontend for about NZ$150 (compaq sff dc7100 $50, Asus GT520 half height fanless card $80, remote $20) - our IT stuff tends to be twice the US$ amount so you could probably build a proper frontend for $70-80 US$.
 
Not small, but works well and sits in the TV stand quite well.
 
Well, at this time, I guess theres nothing further on this thread.  I will goto MythTVtalk an post these questions there as well as join myth-users.
 
I will say the Gen1 appleTV I picked up last weekend from a family member worked great (after being mod'd with firecode).  Connected to MythTV via XBMC, an connected drirectly to my HDHomerun with real time live TV as well as NON Transcoded recordings, also connected to my Plex Media Server on my Mac Mini without issue.  Its small, low power consumption, an after $100 starting cost for Gen2 an a $30 cost for firecode mod, not a bad deal.  An again, its small which is the MOST IMPORTANT part of my wants.  Keep in mind, the power concomption of 3 to 5 computes as you suggested vs 3 to 5 Roku's or ApplesTV is a large power difference.
 
No where have I said that roku's where the end all of my solutions, just what I need to implament now while I work on upgrading each unit to my desired setup.
 
John

---

### Post by nickrout on 2012-11-28
Just remember that a gen 1 appletv is a very different beast to gen 2. Gen 1 always seems to have been a good choice, and sorry didn't realise you were talking about Gen 1. 

I would ask a little more widely before investing in Gen 2 though.

Certainly all the points you make are valid. Do look at the ion options too, they are basically ready out of the box to run both mythfrontend and xbmc, and are pretty low power and $cost.

I believe too that we are near the point where Raspberry Pi plus XBMC PVR plus mythtv may be a valid option, and that certainly meets both your power and cost requirements!

---

### Post by johnfm3 on 2012-11-28
> **nickrout said:**
> Just remember that a gen 1 appletv is a very different beast to gen 2. Gen 1 always seems to have been a good choice, and sorry didn't realise you were talking about Gen 1. 
 
I would ask a little more widely before investing in Gen 2 though.
 
Certainly all the points you make are valid. Do look at the ion options too, they are basically ready out of the box to run both mythfrontend and xbmc, and are pretty low power and $cost.
 
I believe too that we are near the point where Raspberry Pi plus XBMC PVR plus mythtv may be a valid option, and that certainly meets both your power and cost requirements!
 
I will do some more home work on my target devices.  5 months from now when I am ready to purchase the first of the replacement machines, I hope to have a sound plan ahead of me.  For now, I just need to get what I have working.  I will def be keeping my eye out on the Raspberry PI development.  That could make a cool thin client for a video front end as you suggested.
 
Thanks for your suggestions.
John

---

### Post by johnfm3 on 2012-11-29
So I followed the instructions on the line provided below....
 
[http://eternalvoid.net/tutorials/mythtv-autotranscode/](http://eternalvoid.net/tutorials/mythtv-autotranscode/)
 
an now my jobs can transcode to H.264 right after creation.  I did a test on a 30 min video recording an used "top" to watch system resources.  It seems I may need some more ram, but as far as CPU its going to be OK recording 1 stream at a time.
 
End result, 30 min video which started at 3GB has been reduced to 210MB.  I will be testing roku's playabilty tonight when I try to watch the 5pm news.
 
Going to play with the script abit to see about adjusting the settings some if needed.
 
Keep everyone posted.
 
John

---

### Post by nickrout on 2012-11-29
> **johnfm3 said:**
> So I followed the instructions on the line provided below....
 
[http://eternalvoid.net/tutorials/mythtv-autotranscode/](http://eternalvoid.net/tutorials/mythtv-autotranscode/)
 
an now my jobs can transcode to H.264 right after creation.  I did a test on a 30 min video recording an used "top" to watch system resources.  It seems I may need some more ram, but as far as CPU its going to be OK recording 1 stream at a time.
 
End result, 30 min video which started at 3GB has been reduced to 210MB.  I will be testing roku's playabilty tonight when I try to watch the 5pm news.
 
Going to play with the script abit to see about adjusting the settings some if needed.
 
Keep everyone posted.
 
JohnAnd usefully turning your nice HD recording into a small low quality file in the process.

If you want to keep your stuff HD this needs seriously tweaking.```
crop=704:528:12:0
```Why for your recordings?
```
scale=512:384
```Seriously? You have a presumably 1080i or 720p 16:9 recording and you want to do this to it? Madness. Use one of the transcodes from the mailing list or wiki that preserves HD quality at least! At the very least preserve the aspect ratio!

---

### Post by johnfm3 on 2012-11-29
> **nickrout said:**
> And usefully turning your nice HD recording into a small low quality file in the process.
 
If you want to keep your stuff HD this needs seriously tweaking.```
crop=704:528:12:0
```Why for your recordings?
```
scale=512:384
```Seriously? You have a presumably 1080i or 720p 16:9 recording and you want to do this to it? Madness. Use one of the transcodes from the mailing list or wiki that preserves HD quality at least! At the very least preserve the aspect ratio!
 
I dont want HD quality. The majority of the recordings are being viewed by Kids on a 20 in tube TV from 1998 (not widescreen). HD is a waiste for the time being. I would rather that MythTV record in my prefered format to begin with. The only thing we have that has HDMI is 2 HP 23 inch flatscreen monitors for my PC. An thats where many of the movies end up, so I can watch them locally an not be affected by the steam over the network. Even still, I wont waiste more than 2 or 3 gig per 2 hrs of movie.
 
John

---

### Post by nickrout on 2012-11-29
Mythtv, like any pvr, will record what your broadcaster sends.

---

### Post by johnfm3 on 2012-11-29
> **nickrout said:**
> Mythtv, like any pvr, will record what your broadcaster sends.
 
I have come to find that out.  I am still ok with H.264, so thats what I have done.  I will be testing the final product tonight.  The original file wouldnt play on my front end.  So if it plays, then I have what I want.  A working system.
 
John

---

### Post by johnfm3 on 2012-11-30
> **nickrout said:**
> And usefully turning your nice HD recording into a small low quality file in the process.
 
If you want to keep your stuff HD this needs seriously tweaking.```
crop=704:528:12:0
```Why for your recordings?
```
scale=512:384
```Seriously? You have a presumably 1080i or 720p 16:9 recording and you want to do this to it? Madness. Use one of the transcodes from the mailing list or wiki that preserves HD quality at least! At the very least preserve the aspect ratio!
 
 
Hey Nickrout,
So I ran this script last night, an it completed. Now I am able view it on the Roku with buffer issues, but only saw the upper left corner of the video. Unsure if that is a playback issue, or a transcoding issue. The bonus was my ability to play the video without issue.
 
Could the Crop be setup wrong? What if I dont crop or scale, just remove those 2 entries completely such as shown below?
 
```
# first video pass
mencoder -nosound -vf yadif,harddup "$1.tmp" -o /dev/null -ovc x264 -x264encopts pass=1:bitrate=1000:threads=$NUMTHREADS
# second video pass
mencoder -nosound -vf yadif,harddup "$1.tmp" -o $AVIFILE -ovc x264 -x264encopts pass=2:bitrate=1000:threads=$NUMTHREADS

```
 
John

---

### Post by johnfm3 on 2012-11-30
> **johnfm3 said:**
> Hey Nickrout,
So I ran this script last night, an it completed. Now I am able view it on the Roku with buffer issues, but only saw the upper left corner of the video. Unsure if that is a playback issue, or a transcoding issue. The bonus was my ability to play the video without issue.
 
Could the Crop be setup wrong? What if I dont crop or scale, just remove those 2 entries completely such as shown below?
 
```
# first video pass
mencoder -nosound -vf yadif,harddup "$1.tmp" -o /dev/null -ovc x264 -x264encopts pass=1:bitrate=1000:threads=$NUMTHREADS
# second video pass
mencoder -nosound -vf yadif,harddup "$1.tmp" -o $AVIFILE -ovc x264 -x264encopts pass=2:bitrate=1000:threads=$NUMTHREADS

```
 
John
 
Ok, so removing crop an scale failed.  Also noticed that my recordings have commerical detection check, an this script does commercial detection an removal.
 
Its going to be a long weekend....  :-(

---

### Post by johnfm3 on 2012-11-30
So I wander what would happen if I created a user job for the following command....
 
```
/path/to/mencoder input.avi -o output.avi -ovc x264 -x264encopts bitrate=3000 pass=1 nr=2000
```
 
This looks like it would do 1 single pass, an just encode to the desired format an not change the screen size.
 
John

---

### Post by nickrout on 2012-11-30
> **johnfm3 said:**
> Hey Nickrout,
So I ran this script last night, an it completed. Now I am able view it on the Roku with buffer issues, but only saw the upper left corner of the video. Unsure if that is a playback issue, or a transcoding issue. The bonus was my ability to play the video without issue.Possibly because the crop is starting with a 1920x1080 frame and then cropping out a 704x518 rectangle starting at somewhere near the top left corner (x=12,y=0). (Of course you may be starting with a 1280x720 frame, but as you don't seem to be able to tell us what framesize you are starting with, however the effect will be similar, as some simple geometry will tell you). If you read the website you referenced you will see that the scripts are designed for the output of an analogue mpeg2 encoder like the pvr-150. These encoders produce SD video, so the crop will be right for SD frame sizes, not HD frame sizes.>  
 
Could the Crop be setup wrong? What if I dont crop or scale, just remove those 2 entries completely such as shown below?
 modern x264 profiles do a one pass constant quality see for example [http://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide](http://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide)> 
```
# first video pass
mencoder -nosound -vf yadif,harddup "$1.tmp" -o /dev/null -ovc x264 -x264encopts pass=1:bitrate=1000:threads=$NUMTHREADS
# second video pass
mencoder -nosound -vf yadif,harddup "$1.tmp" -o $AVIFILE -ovc x264 -x264encopts pass=2:bitrate=1000:threads=$NUMTHREADS

```
 
John

---

### Post by nickrout on 2012-11-30
> **johnfm3 said:**
> Ok, so removing crop an scale failed.  Also noticed that my recordings have commerical detection check, an this script does commercial detection an removal.
 
Its going to be a long weekend....  :-(Define "failed". What was the error message?

---

### Post by johnfm3 on 2012-11-30
> **nickrout said:**
> Possibly because the crop is starting with a 1920x1080 frame and then cropping out a 704x518 rectangle starting at somewhere near the top left corner (x=12,y=0). 

 modern x264 profiles do a one pass constant quality see for example [http://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide](http://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide)

> **nickrout said:**
> Define "failed". What was the error message?

You an I are on the same thought process.  I need to record a couple mins of Vid an see what the output is an let you know.  Another user posted a way for me to get the vid size.

I looked at the site you provided above, there is an example for fast encoding.  It looks like it doesnt even bother with chopping or scaling.  So will be trying that next.  I am hoping that having the large size in the H.264 format will be all the help I need on the roku.

John

---

### Post by johnfm3 on 2012-12-02
Ok, so I have looked over the starting files which is created by mythtv.

Input #0, mpegts, from '1051_20121201153200.mpg':
  Duration: 00:00:57.50, start: 2558.347944, bitrate: 10160 kb/s
  Program 1 
    Stream #0.0[0x7c0]: Video: mpeg2video (Main), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 38810 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x7c1](eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0x7c2](spa): Audio: ac3, 48000 Hz, stereo, s16, 128 kb/s (visual impaired)

An after running a fast encoding of h264, I am now set like the following...

Input #0, avi, from '1051_20121201153200.mpg.mp4':
  Metadata:
    encoder         : MEncoder SVN-r33713-4.6.1
  Duration: 00:00:57.12, start: 0.000000, bitrate: 4559 kb/s
    Stream #0.0: Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 29.97 fps, 29.97 tbr, 29.97 tbn, 59.94 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 132 kb/s


So I followed the example in the provided link...
```

Profile
[x264]
profile-desc="x264 encoding"
ovc=x264=1
x264encopts=crf=20:threads=0:subq=6:frameref=5:Partitions=all:8x8dct=1:me=umh:bframes=3:b_pyramid=normal:weight_b=1:keyint=25
aspect=16/9
oac=mp3lame=1
lameopts=aq=0:q=0

```

Command Syntax[B]
mencoder -profile x264 input.avi -o output.avi

so the problem I am running into is the time.  Its taking 10 min for every min of video.  So I need to see if I can get it reduced it to at least a 1:1 ratio.

John
[/B]

---

### Post by nickrout on 2012-12-03
> **johnfm3 said:**
> Ok, so I have looked over the starting files which is created by mythtv.

Input #0, mpegts, from '1051_20121201153200.mpg':
  Duration: 00:00:57.50, start: 2558.347944, bitrate: 10160 kb/s
  Program 1 
    Stream #0.0[0x7c0]: Video: mpeg2video (Main), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 38810 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x7c1](eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0x7c2](spa): Audio: ac3, 48000 Hz, stereo, s16, 128 kb/s (visual impaired)

An after running a fast encoding of h264, I am now set like the following...

Input #0, avi, from '1051_20121201153200.mpg.mp4':
  Metadata:
    encoder         : MEncoder SVN-r33713-4.6.1
  Duration: 00:00:57.12, start: 0.000000, bitrate: 4559 kb/s
    Stream #0.0: Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 29.97 fps, 29.97 tbr, 29.97 tbn, 59.94 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 132 kb/s


So I followed the example in the provided link...
```

Profile
[x264]
profile-desc="x264 encoding"
ovc=x264=1
x264encopts=crf=20:threads=0:subq=6:frameref=5:Partitions=all:8x8dct=1:me=umh:bframes=3:b_pyramid=normal:weight_b=1:keyint=25
aspect=16/9
oac=mp3lame=1
lameopts=aq=0:q=0

```

Command Syntax[B]
mencoder -profile x264 input.avi -o output.avi

so the problem I am running into is the time.  Its taking 10 min for every min of video.  So I need to see if I can get it reduced it to at least a 1:1 ratio.

John
[/B]

I did say in Post #7 in this thread that encoding to h264 will take a lot of resources.

OK you say you don't need HD quality, so how about you make the frames smaller? The combination of crop and scale you got from that original script obviously wasn't going to work with 1920x1080 source, for reasons we have already discussed. However there is nothing to stop you coming up with a different scaling.

You are, I think in the USA, so the closest number of lines to your SD TV standard is 480, so scale to a height of 480.

Your material is 16:9 so the width is 480*16/9=853.33, but you need an integer that is a mutiple of 16 (for technical reasons encoding to a multiple of 16 frame size is way quicker). So you want your width to be 848, the nearest multiple of 16.

In short, try scaling to 848x480. It should be a lot quicker.

Also think about your CRF factor. The ffmpeg document I pointed to earlier states: > The range of the quantizer scale is 0-51; where 0 is lossless, 23 is default, and 51 is worst possible. A lower value is a higher quality and a subjectively sane range is 18-28Your present script is using CRF=20, it'll be quicker to increase that to, say 23 and see what happens. Play with it. 23 may be too high, try 22 and 21. 23 may still be too slow, try 24 or 25. There is a tradeoff between speed and quality. Try it on different types of file - cartoons are different to real people are different to action movies etc.

---

### Post by johnfm3 on 2012-12-03
> **nickrout said:**
> I did say in Post #7 in this thread that encoding to h264 will take a lot of resources.
 
OK you say you don't need HD quality, so how about you make the frames smaller? The combination of crop and scale you got from that original script obviously wasn't going to work with 1920x1080 source, for reasons we have already discussed. However there is nothing to stop you coming up with a different scaling.
 
You are, I think in the USA, so the closest number of lines to your SD TV standard is 480, so scale to a height of 480.
 
Your material is 16:9 so the width is 480*16/9=853.33, but you need an integer that is a mutiple of 16 (for technical reasons encoding to a multiple of 16 frame size is way quicker). So you want your width to be 848, the nearest multiple of 16.
 
In short, try scaling to 848x480. It should be a lot quicker.
 
Also think about your CRF factor. The ffmpeg document I pointed to earlier states: Your present script is using CRF=20, it'll be quicker to increase that to, say 23 and see what happens. Play with it. 23 may be too high, try 22 and 21. 23 may still be too slow, try 24 or 25. There is a tradeoff between speed and quality. Try it on different types of file - cartoons are different to real people are different to action movies etc.
 
Yes, your right.  You did state it would be resources intensive.  I am hoping for a 1:1 raitio of time needed per length of movie.
 
So in the original script, there is 1 pass for pulling audio, 2 passes for video, an the final pass puts it all together.  In my single pass provided in my last post, there was no video change, just convert to mp4.
 
In my view, going over a video 4 times to create a final product is going to be slower than going over it 1 time.  Am I correct in this?
 
What if I do not change the format, an just reduce the video size (using scale setting) within the original mpg2 then allow plex to transcode to H264 in real time for Roku's?  An per your suggestion, try reducing it too 848x480.  I will be following this post with one providing the video requirements that the roku is looking for.
 
As alwayst, thank for helping me sort thru this mess to understand what I am working on.
 
John
 
BTW: Your correct in my being from USA.

---

### Post by johnfm3 on 2012-12-03
[IMG]http://i1128.photobucket.com/albums/m486/CalvinMcGowan/RokuVideoFormats27.jpg[/IMG]

---

### Post by johnfm3 on 2012-12-03
Ok, so I just tried the following...
 
```
mencoder -oac copy -ovc copy -vf scale=1280:720 inputvid.mpg -o outputvid.mpg
```
 
The end result, I dropped one of the audio streams. But the video size never changed.
```
    Stream #0.0[0x7c0]: Video: mpeg2video (Main), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 38810 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.2[0x7c2](spa): Audio: ac3, 48000 Hz, stereo, s16, 128 kb/s (visual impaired)
```
 
```
    Stream #0.0[0x7c0]: Video: mpeg2video (Main), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 38810 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x7c1](eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0x7c2](spa): Audio: ac3, 48000 Hz, stereo, s16, 128 kb/s (visual impaired)
```
 
So what am I doing wrong when I try to reduce the video size to 1280x720?
I am looking at this as a result seeing the video size in the table I showed above for H264 HD.
 
John

---

### Post by nickrout on 2012-12-04
-ovc copy means exactly that, copy the video stream unchanged.

In the first script (the copied one) the slow bits are the two pass video encoding.  Two pass is not needed with CRF, so using CRF speeds things up.

I'll ask again, wouldn't just using the new services api be easier?

---

### Post by geomansero on 2012-12-04
[http://myipb.ru/](http://myipb.ru/)

---

### Post by rDwyP44y on 2012-12-04
I have this same issue, but it seems that I might has messsed up something, it worked before...

---

### Post by johnfm3 on 2012-12-04
> **nickrout said:**
> -ovc copy means exactly that, copy the video stream unchanged.
 
In the first script (the copied one) the slow bits are the two pass video encoding. Two pass is not needed with CRF, so using CRF speeds things up.
 
I'll ask again, wouldn't just using the new services api be easier?
 
-ovc copy:  So I noticed.  Aparently, when you set it to copy the -vf (video filters) setting is ignored.
 
What new services API?  Is it in the new version of Myth (I am on 0.24) ?  If so, I have to pass until support for XBMC is there.  The only device I have that works almost perfectly is my Gen 1 Apple TV an it wont connect to the Myth service in 0.25.
 
So I found that if I choose -ovc lavc an -vf scale=960:544that I can encode a 1 min video in just around 1 min 10 seconds.  That is probably the best it gets.
 
John

---

### Post by johnfm3 on 2012-12-04
So I came accross the following page which provides an old script from 2006 on mythTV wiki...
 
[http://www.mythtv.org/wiki/Transcoding_for_the_PDA](http://www.mythtv.org/wiki/Transcoding_for_the_PDA)
 
At first glance, it looks like a good solution for what I need.  Gunna do some digging on this.
 
Heres the code.  Thoughts?
```
#!/bin/sh
 # pdatranscode
 #
 # created by Jeff Volckaert (inspired by Zach White) 
 # modified 11/10/06
 VIDEODIR=$1
 FILENAME=$2
 TITLE=$3
 # Remove non-alpha characters from TITLE
 TITLE=${TITLE//[^a-zA-Z0-9]/}
 STARTTIME=$4
 SUBTITLE=$5
 # Remove non-alpha characters from SUBTITLE
 SUBTITLE=${SUBTITLE//[^a-zA-Z0-9]/}
 
 # Sanity checking, to make sure everything is in order.
 if [ -z "$VIDEODIR" -o -z "$FILENAME" ]; then
         echo "Usage: $0 <VideoDirectory> <FileName> "<Title>" <Starttime>"
         exit 5
 fi
 if [ ! -f $VIDEODIR/$FILENAME ]; then
         echo "File does not exist: $VIDEODIR/$FILENAME"
         exit 6
 fi
 
 # Transcode the file (Uncomment the method you want to use)
   
 # Transcode using Myth's Transocde for Low Quality
 # mythtranscode -i  $VIDEODIR/$FILENAME -o  $VIDEODIR/pda/$TITLE-$STARTTIME.avi -l -p 29
 
 # Transcode using mencoder Xvid
 # mencoder -vf scale=320:240 -oac mp3lame -lameopts mode=0:cbr:br=96 -af volnorm -srate 32000 -ovc    xvid -xvidencopts bitrate=300 -o $VIDEODIR/pda/$TITLE-$STARTTIME-$SUBTITLE.avi $VIDEODIR/$FILENAME -quiet
 
 # Transcode Using lavc's mpeg4 (this is what I use)
 mencoder -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=300:vhq:vpass=1 -vf scale=320:240 -oac lavc   -lavcopts acodec=ac3:abitrate=128 -ffourcc DX50 -o $VIDEODIR/pda/$TITLE-$STARTTIME-$SUBTITLE.avi $VIDEODIR/$FILENAME -quiet
   
 
 # Transcode using FFmpeg for Ipod Touch
 #nice -+19 ffmpeg -i  $VIDEODIR/$FILENAME -f mp4 -r 30 -vcodec mpeg4 -b 384 -qmin 3 -qmax 5 -g 300   -acodec aac -ar 44100 -ab 192 -s 320x240 -aspect 16:9 -title $TITLE $VIDEODIR/pda/$TITLE-$STARTTIME.mp4 -v -1
 
 
 # Transcode using Mencoder for Ipod Touch
# nice -+19 mencoder -ofps 25 -of lavf -lavfopts format=mp4 -af lavcresample=44100 -vf-add harddup -vf-add scale=320:240 -oac lavc -ovc lavc -lavcopts aglobal=1:vglobal=1:acodec=libfaac:abitrate=128:vcodec=mpeg4:vbitrate=384:keyint=25 -o $VIDEODIR/pda/$TITLE-$STARTTIME-$SUBTITLE.mp4 $VIDEODIR/$FILENAME -quiet
 
 
 # Transcode for Dell PDA
 # nice -+19 mencoder -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=256:vhq -vf scale=320:240 -oac lavc -lavcopts acodec=mp3:abitrate=128 -ffourcc DX50 -o $VIDEODIR/pda/$TITLE-$STARTTIME-$SUBTITLE.avi $VIDEODIR/$FILENAME -quiet
 
 
 chmod 664 $VIDEODIR/pda/$TITLE-$STARTTIME-$SUBTITLE.avi
 
 ERROR=$?
 if [ $ERROR -ne 0 ]; then
         echo "Transcoding failed for ${FILENAME} with error $ERROR"
         exit 3
 fi

```
 
John

---

### Post by FakeOutdoorsman on 2012-12-04
This is commented out, but the ffmpeg command uses ancient syntax:
```
 # Transcode using FFmpeg for Ipod Touch
 #nice -+19 ffmpeg -i  $VIDEODIR/$FILENAME -f mp4 -r 30 -vcodec mpeg4 -b 384 -qmin 3 -qmax 5 -g 300   -acodec aac -ar 44100 -ab 192 -s 320x240 -aspect 16:9 -title $TITLE $VIDEODIR/pda/$TITLE-$STARTTIME.mp4 -v -1
```
 
Current syntax for ffmpeg will be:
```
ffmpeg -i input -f mp4 -vcodec libx264 -preset medium -crf 24 -profile:v baseline -level 30 -acodec aac -strict experimental -ab 192k -s 320x240 -metadata title="Example Title" output
```
Not tested with the repo versions.

---

### Post by johnfm3 on 2012-12-04
> **FakeOutdoorsman said:**
> This is commented out, but the ffmpeg command uses ancient syntax:
```
 # Transcode using FFmpeg for Ipod Touch
 #nice -+19 ffmpeg -i  $VIDEODIR/$FILENAME -f mp4 -r 30 -vcodec mpeg4 -b 384 -qmin 3 -qmax 5 -g 300   -acodec aac -ar 44100 -ab 192 -s 320x240 -aspect 16:9 -title $TITLE $VIDEODIR/pda/$TITLE-$STARTTIME.mp4 -v -1
```
 
Current syntax for ffmpeg will be:
```
ffmpeg -i input -f mp4 -vcodec libx264 -preset medium -crf 24 -profile:v baseline -level 30 -acodec aac -strict experimental -ab 192k -s 320x240 -metadata title="Example Title" output
```
Not tested with the repo versions.
 
Thanks for the heads up.  I will be sure to correct it in the script.
 
The very first line is /bin/sh, shouldnt that be /bin/bash?
 
John

---

### Post by nickrout on 2012-12-04
> **johnfm3 said:**
> Thanks for the heads up.  I will be sure to correct it in the script.
 
The very first line is /bin/sh, shouldnt that be /bin/bash?
 
JohnDepends which shell you want it to run under?

---

### Post by johnfm3 on 2012-12-04
> **nickrout said:**
> Depends which shell you want it to run under?
 
I am comfortable with bash.  I think the default shell is bash on the machine I am working on.  Unsure how to tell.  But I know that syntax an how the shell handles variables can change between the shells.  While at amazon, I had to write some in Korn Shell (ksh) as a result.  Saddly, I dont understand the full reasons as to why.
 
John

---

### Post by nickrout on 2012-12-04
> **johnfm3 said:**
> -ovc copy:  So I noticed.  Aparently, when you set it to copy the -vf (video filters) setting is ignored.Well of course you can't copy a stream AND scale it. YOu'll need to speciy an output codec if you want to scale> 
 
What new services API?  Is it in the new version of Myth (I am on 0.24) ?  If so, I have to pass until support for XBMC is there.  The only device I have that works almost perfectly is my Gen 1 Apple TV an it wont connect to the Myth service in 0.25.The services api in 0.25 onwards. XBMC works with 0.25 - what method of connecting are you using and what version of XBMC?> 
 
So I found that if I choose -ovc lavc an -vf scale=960:544that I can encode a 1 min video in just around 1 min 10 seconds.  That is probably the best it gets.
 
JohnI thought you wanted h264 encoding and SD scaling? I really can't figure out what you want.

---

### Post by johnfm3 on 2012-12-04
> **nickrout said:**
> The services api in 0.25 onwards. XBMC works with 0.25 - what method of connecting are you using and what version of XBMC?
 
My appletv has mythbox plugin installed on XBMC an its not currently compatible with MythTV 0.25.  Since my AppleTV is the best setup which is working on Real Time Live TV as well as recordings an most my videos, I am hesitant to upgrade mythtv to 0.25.
 
[http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)
 
 
> **nickrout said:**
> I thought you wanted h264 encoding and SD scaling? I really can't figure out what you want.
 
 
My wants/needs are morphing.  It looks as if Plex Media Server is transcoding all types of recorded video to the Roku.  So I am wandering about formatting the video which will be transcoded in real time anyways so its not so harsh.  My thought is just simply to reduce the video screen size to see if it will reduce the work load against the myth server.
 
John

---

### Post by nickrout on 2012-12-04
> **johnfm3 said:**
> I am comfortable with bash.  I think the default shell is bash on the machine I am working on.  Unsure how to tell.  But I know that syntax an how the shell handles variables can change between the shells.  While at amazon, I had to write some in Korn Shell (ksh) as a result.  Saddly, I dont understand the full reasons as to why.
 
John```
ls -l `which sh`
lrwxrwxrwx 1 root root 4 2010-08-25 18:15 /bin/sh -> dash
```

korn has many adherents, and the differences in shells are subtle but important if you are writing complex scripts (if they are that complex python is worth learning.)

---

### Post by nickrout on 2012-12-04
> **johnfm3 said:**
> My appletv has mythbox plugin installed on XBMC an its not currently compatible with MythTV 0.25.  Since my AppleTV is the best setup which is working on Real Time Live TV as well as recordings an most my videos, I am hesitant to upgrade mythtv to 0.25.
 
[http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)
 
 

 
 
My wants/needs are morphing.  It looks as if Plex Media Server is transcoding all types of recorded video to the Roku.  So I am wandering about formatting the video which will be transcoded in real time anyways so its not so harsh.  My thought is just simply to reduce the video screen size to see if it will reduce the work load against the myth server.
 
JohnLet plex do it's thing. It will be more efficient to let the transcoding happen once (by plex).

---

### Post by johnfm3 on 2012-12-04
> **nickrout said:**
> Let plex do it's thing. It will be more efficient to let the transcoding happen once (by plex).
 
Agreed. But cutting a circle out of a square is far more work than cutting out of a octogon.
 
My thought is if i can CUT the FAT out of the original files, it wont be so harsh.
 
As it is now, when I view the Original MPEG2 files (transcoded via Plex) on my Roku's, the stream has to reload about every 2 min. Probably due to way too much data. An the reload can take as long as 30 sec.  So my current thought is to get the original files stripped an preped so that when Plex does its thing, its not process heavy an it can move forward with the stream.
 
john

---

### Post by nickrout on 2012-12-04
> **johnfm3 said:**
> Agreed. But cutting a circle out of a square is far more work than cutting out of a octogon.
 
My thought is if i can CUT the FAT out of the original files, it wont be so harsh.
 
As it is now, when I view the Original MPEG2 files (transcoded via Plex) on my Roku's, the stream has to reload about every 2 min. Probably due to way too much data. An the reload can take as long as 30 sec.  So my current thought is to get the original files stripped an preped so that when Plex does its thing, its not process heavy an it can move forward with the stream.
 
johnSO what you need to figure out is what is holding up the process. Is it a dodgy network or is it a slow processor. Look at the output of top while plex is transcoding, and see if the processor is overloaded.

If you want to do a lot of transcoding, via the services api, or plex, or mencoder or however you want to do it, you NEED a grunty processor and lots of RAM. I am not sure what backend you are running, if you have posted that I haven't reviewed the 5 pages of posting to check. 

Frankly you have 2 choices, run a frontend with a proper processor or GPU so you can decode your video OR run a grunty backend and transcode. Myth is designed for the former, but the services api is evidence of growing support for the latter.

By the way the mythbox plugin works for me with (a) xbmc 12 (currently beta but works well, not sure about availability on ATV) and (b) the mitchcapper version of mythbox ([https://github.com/mitchcapper/mythbox](https://github.com/mitchcapper/mythbox))

You might also want to try the latest xbmc with PVR support and the mthtv pvr plugin, or the myth:// protocol support.

---


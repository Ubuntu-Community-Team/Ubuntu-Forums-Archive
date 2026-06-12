---
title: "Video render / output tips from Pitivi wanted!"
date: 2010-06-08
forum: Multimedia Software
---

### Post by cdaringe on 2010-06-08
Hey everybody,

I am using ffmpeg for screen capture and loading my captures into Pitivi for easy cutting & sound tweaks.

My screen capture command is as follows, and gets me beautiful video:
```

ffmpeg -f alsa -ac 2 -i hw:0,0 -f x11grab -r 20 -s 1360x768+0+0 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -y TITLE_OF_VIDEO.mkv

```

After splicing and adding new audio, I'd like to know some of the best setups for getting clear audio/video out as close to the native recordings' quality/resolution as possible.  I'm messing with the parameters, and compression is making things ugly.  How should I retain good, grain-free quality after changes in Pitivi?  I intend to upload some videos on the yewtubes, and don't want recompression into their flv to make things any less clear.  Perhaps Pitivi is the wrong choice in the first place?  It'd be great if I could just splice and combine video, then overlay the audio tracks somehow?

Thoughts?

---

### Post by theSuperman on 2010-11-10
Did you ever figure out some good rendering settings? All my video outputs look horrible!

---

### Post by cdaringe on 2010-11-10
nah.  I wish!  I'd still care to know :(

---

### Post by theSuperman on 2010-11-11
Damn. I tried using Cinelerra (had to compile from source for 10.10) and it crashes all the time. Pitivi is so much easier to use. After experimenting, I finally came up with this:
-Container: MP4Muxer[mp4mux]
-Audio Codec: Ffmpeg ALAC (Apple lossless Audio Encoder) encoder [ffenc_alac]
-Video Codec: Ffmpeg MPEG-4 part 2 encoder[ffenc_mpeg4]
  I changed the video codec bit rate to "10300000"
Of course, the video was quite large (1min30secs was 110megs), but it looked alright. I needed to upload to youtube, so I wanted pretty good quality.

---

### Post by patocardo on 2010-11-23
I've been trying all day long with different non-success results. Anyone knows what parameters do I need to join and render several videos downloaded from youtube?
Most of codecs just don't allow the program to start render, others change the speed of video in relation to audio, others suddenly stop rendering and others are not understandable by player. I still have a lot of containers and codecs to try, but I would like to avoid other day. Does anyone have done it successfully?

---

### Post by manco on 2011-06-19
> **theSuperman said:**
> Container: MP4Muxer[mp4mux]
Audio Codec: Ffmpeg ALAC (Apple lossless Audio Encoder) encoder [ffenc_alac]
Video Codec: Ffmpeg MPEG-4 part 2 encoder[ffenc_mpeg4]
I changed the video codec bit rate to "10300000"
Thanks a million! I had just about given up on PiTiVi until I came across this :)

---

### Post by srihari29691 on 2011-11-15
**changing the bitrate fixed things for me! :)**
thanks a ton!

however, youtube supported formats says-

.MPEG4, 3GPP and MOV files - Typically supporting h264, mpeg4 video codecs, and **AAC audio codec**

but mine has LAME .mp3 audio codec...
I'm afraid the youtube audio quality wont come out well...

---

### Post by cdaringe on 2011-11-15
well make sure to let us all know!

---

### Post by srihari29691 on 2011-11-29
it worked beautifully!
my youtube video came out in HD! :P

---

### Post by deyanyosifov on 2011-12-24
The solution of theSuperman did not work for me as for some reason PiTiVi would not save mp4 files correctly but I found out another set of settings that worked perfectly :
1. Container format: FFmpeg MPEG-1 System.
2. Video codec: FFmpeg MPEG-1. In the Advanced Tab one could increase the bitrate to 10300000 as theSuperman suggested and that produces fine results but the output file is very large. I found out another solution: Do not change the bitrate. Change Emoding pass/type to Constant Quantizer instead of Constant bitrate. Increase the Minimum Quantizer setting to 26 (the setting is located some way below in the list of options, its default value is 2).
3. Audio codec: LAME mp3.

That's it :-D :-D :-D! The output file had very good quality, was also large, but smaller than if increasing the bitrate. 4:01 minutes, 1920:1440 in 111 MiB. I haven't tried yet if selecting a somewhat smaller value for the constant quantizer will keep the same video quality at a smaller file size. I'll give it a try now. Anyway, maybe it is a good idea if PiTiVi could come with a higher default value for the constant quantizer so that new users do not become frustrated with the program at the very beginning.

---

### Post by deyanyosifov on 2011-12-24
I tried out with Constant quantizer set to 20 - the quality was just as good as last time and the file size was smaller.

---

### Post by wagoner on 2012-01-23
I started with an .AVI file that I shot with my cannon camera.  Then, I used the FFmpeg MPEG-1 System and it worked pretty well.  The audio with L.A.M.E. mp3 was choppy, so I switched the audio encorder to FFmpeg MP2 (MPEG layer 2), and that solved the problem.  I set the Minimum Quantizer for the video encoder to 26 (actually 25, but close enough), like he recommended in the post above.

I couldn't get MP4 to work at all.  It would just hang.

---


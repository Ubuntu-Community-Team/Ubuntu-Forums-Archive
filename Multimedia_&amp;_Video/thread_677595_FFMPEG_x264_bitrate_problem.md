---
title: "FFMPEG x264 bitrate problem"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Shmifty on 2008-01-25
My video is encoding at 2000+kbps, but I didn't set it that high, I heard you don't need even really need 2000kbps for most videos. 

This is the command I used

> ffmpeg -i /media/sdb1/OLD_SCHOOL/VIDEO_TS/VTS_01_1.VOB -an -pass 1 -vcodec h264 -b 1250k -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me epzs -subq 1 -trellis 0 -refs 1 -bf 3 -b_strategy 1 -coder 1 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 1250k -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 /media/sdb1/Old.mp4

Any suggestions? (I'm fairly new to encoding and any advice on what bitrate to use would be much appreciated)

EDIT: I was wondering what the command for a high quality and relatively low size (720x480 resolution x264 mp4) Also I believe this video is encoding at 60fps instead of the 30000/1001 fps I want it to run at, how would I change that (I tried -re to run in the native frame rate, but that wouldn't do it either)?

---

### Post by philc on 2008-01-25
You could try specifying a maxbitrate to limit the bitrate to 1250k if that's what you want to do.

You're not specifying an audio codec or bitrate in the example you've given. Therefore copying the original audio from the VOB file could account for the extra TOTAL bitrate you're seeing.

For a better x264 quality encode you could try some of the following:

- set subq to 5 or 6
- enable CABAC with -codec ac 
- use 2 pass encoding rather than 1

If you use the following command, FFmpeg will show you the attributes of your video file and you can see the fps for sure:

ffmpeg -i /media/sdb1/Old.mp4

---

### Post by Shmifty on 2008-01-25
I don't know how to do two pass encoding

This is the new command I'm using:
> ffmpeg -i /media/sdb1/OLD_SCHOOL/VIDEO_TS/VTS_01_1.VOB -threads auto -pass 1 -vcodec libx264 -b 1250k -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me epzs -subq 5 -trellis 0 -refs 1 -bf 3 -b_strategy 1 -coder 1 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 1250k -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -r 30000/1001 -coder ac -async 50 -acodec libfaac -ar 48000 -ac 2 -ab 128k /media/sdb1/Old.mp4


---

### Post by philc on 2008-01-25
Be sure to remove -coder 1 now that you have added -coder ac

For 2 pass simply direct pass 1 to /dev/null for the output, then re-run the same ffmpeg command but with -pass 2 and the real output destination. The first pass will write a log file with information about your input video that will be used in the second pass.

---

### Post by Shmifty on 2008-01-25
Ok now that I have everything else working I was wondering what the recommended bitrate was for DVD -> mp4 conversions. I want it to be good quality, but I also don't want it taking up too much space.

You mind posting what you think to be a highly optimized code with preferred bitrates?

---

### Post by eye208 on 2008-01-25
> **Shmifty said:**
> Ok now that I have everything else working I was wondering what the recommended bitrate was for DVD -> mp4 conversions. I want it to be good quality, but I also don't want it taking up too much space.
If you are more concerned about quality than file size, you can use constant quantizer or constant rate factor encoding. This requires only one pass but makes the file size somewhat unpredictable. But the video quality will be on a constant level all the time. The encoder will vary the bitrate as needed to keep that constant quality level.

You can encode small parts of the video to preview the quality and find the best quantizer or rate factor setting.

If you intend to write the MP4 file to a CD, stick with 2-pass encoding and choose the target bitrate so that the final file will be just below 700 MB large (including audio).

---

### Post by Shmifty on 2008-01-25
When I say good quality I just want it to be viewable without noticeable blocks. Plus I will be encoding from DVDs so I don't need anything that tries to make the quality better than that.

---

### Post by eye208 on 2008-01-25
> **Shmifty said:**
> When I say good quality I just want it to be viewable without noticeable blocks.
Unlike Xvid/DivX, low bitrates with H.264 will not result in block artifacts but in blurred details. You need to do some test encodings to find out how much blurring you find acceptable.

---

### Post by philc on 2008-01-27
> **Shmifty said:**
> 
You mind posting what you think to be a highly optimized code with preferred bitrates?

OK, this is what I would use, but am willing to learn from others too if they have something different to contribute.

ffmpeg -y -i input_file -an -v 1 -threads auto -vcodec libx264 -deinterlace -b 5000k -bt 175k -flags +loop -coder ac -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq \'blurCplx^(1-qComp)\' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 5000k -bufsize 2M -cmp 1 -s 720x480 -f mp4 -pass 1 /dev/null

ffmpeg -y -i input_file -v 1 -threads auto -vcodec libx264 -deinterlace -b 5000k -bt 175k -flags +loop -coder ac -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq \'blurCplx^(1-qComp)\' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 5000k -bufsize 2M -cmp 1 -s 720x480 -acodec libfaac -ab 256k -ar 48000 -ac 2 -f mp4 -pass 2 new_file.mp4

Now, that's an output bitrate of about 5Mbps, which may be overkill for you. It really depends on what device you're going to be viewing the final files - a big TV vs an iPod?

DVDs are encoded at around 8-9Mbps. Old style VHS tapes are more like equivalent to 2Mbps. So, the 5Mbps is what I would personally use for x264 files that I intended watching on a largish TV screen, but served from my PC or media centre. You'll get a pretty good picture, and the file sizes will be significantly smaller than the VOB files on your DVD.

---

### Post by FakeOutdoorsman on 2008-01-27
If you want to test a certain number of frames instead of encoding the whole video use -vframes x, where x is the number of frames to encode:
```
-vframes 300
```

This example would encode the first 300 frames.

---

### Post by FakeOutdoorsman on 2008-01-27
> **philc said:**
> OK, this is what I would use, but am willing to learn from others too if they have something different to contribute.

Building on what philc came up with here is an alternate example which includes using "b frames" (this example is untested):

```
ffmpeg -y -i input_file -an -v 1 -threads auto -vcodec libx264 -deinterlace -b 5000k -bt 175k -flags +loop -coder ac -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me **epzs** -subq 1 -me_range 21 -chroma 1 -slice 2** -bf 3 -b_strategy 1** -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 5000k -bufsize 2M -cmp 1 -s 720x480 -f mp4 -pass 1 /dev/null

ffmpeg -y -i input_file -v 1 -threads auto -vcodec libx264 -deinterlace -b 5000k -bt 175k -flags +loop -coder ac -refs 5 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2** -bf 3 -b_strategy 1** -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 5000k -bufsize 2M -cmp 1 -s 720x480 -acodec libfaac -ab 256k -ar 48000 -ac 2 -f mp4 -pass 2 new_file.mp4
```

Differences are bold. Changed first pass motion estimation to the faster "epzs" setting.  More specific x264 setting descriptions can be found at [Encoding with the x264 codec]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html").  It's for MEncoder, but it's still useful.  Also refer to the x264 specific ffmpeg -flags2 settings.

---


---
title: "MTS/MT2S to MKV (Esp. Applicable to Sony HD Camcoders)"
date: 2010-11-21
forum: Multimedia Software
---

### Post by control_guy on 2010-11-21
After spending many frustrating hours, I finally found a solution to easily re-mux m2ts/mts files produced by Sony HDR-SR12 or other similar camcoders in order to stream them smoothly over DLNA to Samsung C-Series (55C8000) TV in full HD quality. But the solution is generic and can be used for any rendered.

[SIZE="5"]Problem:[/SIZE]

First the problem: Above mentioned Sony camcoder produces 1920x1080, 60i video. However, the time-stamps on the frames in each interlaced field are wrong, both frames of a filed having same time-stamp. This is very problematic for almost all rendering devices.

My first approach was to re-encode these mts files using Handbrake to convert to m4v. This worked though at a heavy computing cost. The conversion is very intensive and for 50GB of videos could easily take more than 12 hours on a core-2 processor.

One day, I was browsing Ubuntu forums, I came across [this]("http://ubuntuforums.org/showthread.php?t=1572473") thread. This actually produced the re-muxed file in a fraction of a second as opposed to **re-encoding** with Handbrake that took very long time.

But there are two problems in the above solution:
1. It is using mencoder + lavf, a known broken combination in presence of B-frames.
2. It does not allow to copy the subtitle track (PGS) that Sony camcoder produces. This subtitle track is very important as it contains the recording date/time information which will be valuable when using these videos in future.

[SIZE="5"]Solution:[/SIZE]

The following solution overcomes all the above-mentioned problems, is rock-stable and preserves the sub-title stream as well. I use ffmpeg to simply copy all the streams and output them in an mkv container. No information is lost/re-encoded. Here is the simple answer (as often observed in scientific research, the useful answer to a complex problem can often be stated very simply :) ):

```
ffmpeg -i input.mt2s -scodec copy -acodec copy -vcodec copy -f matroska input.mkv
```

I have written a script that converts all the m2ts files in a subfolder to mkv. The script is as below:

```
#!/bin/bash

# m2tstomkv_subs (Fix the faulty fps (dual frames in the interlaced fields with same time-stamps) and repackage in matroska mkv container)

time {
# remux m2ts movies into mkv with ffmpeg
for i in *.m2ts; do 
ffmpeg -i $i -scodec copy -acodec copy -vcodec copy -f matroska `basename $i .m2ts`.mkv;
echo "Conversion done";
done
}
exit;

```

The conversion is lightening fast. Finally I am able to watch the videos in their true quality.

I will be glad if this information helps someone facing similar issues.

---

### Post by WonderStivi on 2011-01-31
You, sir, are a genius!

---

### Post by cotcot on 2011-04-17
> **control_guy said:**
> 

First the problem: Above mentioned Sony camcoder produces 1920x1080, 60i video. However, the time-stamps on the frames in each interlaced field are wrong, both frames of a filed having same time-stamp. This is very problematic for almost all rendering devices.


You made a very interesting post.

A question : do you have the possibility to select between 25p and 50i on your camcorder ?
On mine (Canon HF100) i have the possibility to select (24p, 25p, 50i). The 25p is filed as 50i but with the frames each 1/25 s split in 2 half frames. Maybe that the reason for the same time stamp each 2 half frames.

---

### Post by biodiesel-bri on 2011-05-21
FWIW this script isn't working for some 1080i content I just downloaded.  ffmpeg seems to have a long history of bugs with the -copy flag.

Here's the error I got:
[matroska @ 0x1141ef0]st:0 error, non monotone timestamps 40 >= 40
av_interleaved_write_frame(): Operation not permitted 

Any other ideas would be appreciated.

---

### Post by BicyclerBoy on 2011-05-21
Unless the situation has changed recently...
ffmpeg can not vcodec copy h264 material.

Was the OP material H264 HD or mpeg2 HD ?

HD m2ts is most commonly a form of H264 in a modifed mpeg-2-ts container.
The ffmpeg copy method (muxer) which is unable to handle out of order frames etc.

To use ffmpeg with h264 you must transcode so the decoder is used.

The above could be out of date..

Have you tried AviDemux to re-write the file (not transcode) ?

---


---
title: "Video Compression"
date: 2009-02-22
forum: Multimedia Software
---

### Post by jlabomb on 2009-02-22
I just wanted to see what kind of ideas can pop up on this forum. At my job they have been seeking to have a laptop with a wireless Verizon card to upload video that will be about 1:30 to 2:00 long. Their test files are over 100 MB's and I found that an unacceptable size for such a short video. The solution they had was some sort of acceleration software that will be $150 license for the main download site and $50 per upload laptop to upload the video in a timely manner. They are smart people but I figured compressing the video with divx or xvid would be better and cheaper than acceleration software. I was wondering if anyone had a better solution to transfer video from a field laptop back to the main building and how long the transfer would take. Also the highest quality video possible is needed for broadcast on TV. I think as long as the quality is not very noticeably bad it will be fine. Any input is appreciated. Thanks.

---

### Post by davidsrsb on 2009-02-22
Best compression size/quality does not go with real time

divx/xvid is about as good as it gets for video compression

---

### Post by FakeOutdoorsman on 2009-02-23
x264 will provide better quality for size than xvid.  The get the best results, you will have to compile FFmpeg and x264, but that isn't very hard to do:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

An advantage to compiling is the inclusion of the new libx264 presets which make it easy to encode high quality video.  There are even several lossless video presets (max, slow, slower, medium, fast, ultrafast). They all give the same resulting quality, but slower ones will give better compression:
```
ffmpeg -i input -vcodec libx264 -acodec libfaac -ab 256k -vpre lossless_medium -threads 0 output.mp4
```

---

### Post by FakeOutdoorsman on 2009-02-23
I just tried a lossless preset on a 35 second DV video.  The resulting video looked great, but the file size wasn't much different than the original and the encode took a long time (I have a slow single-core CPU).  I guess I shouldn't be surprised because lossy to lossless should usually make a bigger file.  Probably not what you want.

Another option is to use one-pass CRF with -crf 18 (anything lower than 18 might be overkill, but you'll have to test):
```
ffmpeg -i input -vcodec libx264 -acodec libfaac -ab 256k -vpre hq -crf 18 -threads 0 output.mp4
```

---

### Post by xzero1 on 2009-02-23
You can use a hardware h.264 encoder such as the hauppage hdpvr which uses a negligible amount of cpu. It gives fairly good results using variable bitrates as low as 2-3Mbps.

---

### Post by jbrown96 on 2009-02-23
Licensing will be a big issue. You cannot use FFMPEG legally in most countries. All video and audio codecs (except ogg theora and vorbis) are patented and you must have a license to encode and decode them. 

I wouldn't want to open my company to additional liabilities, so I doubt you will be able to do it for free, but I'm sure you can do it cheaper. Check out licenses from Fluendo for various codecs.

Like an earlier poster said, x264 will give you the best compression at really good quality, but it will be CPU-intensive.

---

### Post by FakeOutdoorsman on 2009-02-23
> **jbrown96 said:**
> You cannot use FFMPEG legally in most countries.
Where did you read this at?  I don't believe its illegal to use FFmpeg in any country, but it may be infringement if you commercially use certain implementations of patented encoders without paying royalty fees to the appropriate agency, such as [MPEG-LA](http://www.mpegla.com).  More info: [FFmpeg License and Legal Considerations](http://ffmpeg.org/legal.html).

---

### Post by davidsrsb on 2009-02-24
See [http://compression.ru/video/codec_comparison/subjective_codecs_comparison_en.html](http://compression.ru/video/codec_comparison/subjective_codecs_comparison_en.html)

There is very little difference between x264 and divx

---

### Post by kamolt on 2009-02-24
In the past I transcoded all my video's to divx or xvid but then I discovered x.264 (H.264) which gives in my opinion a much better picture. Avidemux is a great tool for video encoding and editing and it handles x.264 as well as xvid. To transcode a 1.5 hrs movie from mpeg to x.264 (2pass) it takes approx 2 hours with my core i7 920 platform. I don't notice any difference between encoded version and the original.

---

### Post by binbash on 2009-02-24
> **FakeOutdoorsman said:**
> Where did you read this at?  I don't believe its illegal to use FFmpeg in any country, but it may be infringement if you commercially use certain implementations of patented encoders without paying royalty fees to the appropriate agency, such as [MPEG-LA](http://www.mpegla.com).  More info: [FFmpeg License and Legal Considerations](http://ffmpeg.org/legal.html).

No it is not right, It is free here!

---

### Post by FakeOutdoorsman on 2009-02-24
> **davidsrsb said:**
> See [http://compression.ru/video/codec_comparison/subjective_codecs_comparison_en.html](http://compression.ru/video/codec_comparison/subjective_codecs_comparison_en.html)

There is very little difference between x264 and divx
That comparison is more than three years old.  x264 is currently at r1114 compared to that subjective review's usage of what I'm guessing is r352.  Much has changed since then.  They also use different compression standards: MPEG-4 Part 2 (DivX) and MPEG-4 Part 10 / MPEG-4 AVC (H.264).

---

### Post by jlabomb on 2009-04-27
Thanks for all the replies, it looks like our company is going to use Skype to feed the video. I have for a phone but never used it for video.

---


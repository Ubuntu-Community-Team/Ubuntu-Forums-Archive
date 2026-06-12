---
title: "Add text to a video"
date: 2011-10-14
forum: Multimedia Software
---

### Post by Dead root on 2011-10-14
Hi,

I am looking for a way to convert and add some text(watermark) to videos in Linux.

I know ffmpeg can be used to convert video but i does not add text or water mark to video. 

P.S : I want to use it using command line only. and not a visual interface so I can test it on my server.

So what are my options?

Thanks

---

### Post by FakeOutdoorsman on 2011-10-14
I'm going to assume you're using Ubuntu Oneiric Ocelot 11.10.

1. Install **libfreetype** files for FFmpeg:
```
sudo apt-get install libfreetype6-dev
```

2. Compile FFmpeg. The version from the repository does not include the **drawtext** filter.

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

In **Step 5** from the guide add:
```
--enable-libfreetype
```

Then continue with the guide.

3. Your command. See the [libavfilter documentation](http://ffmpeg.org/libavfilter.html#SEC27) for a description of the options and some examples.

---


---
title: "Avi Remuxing to MP4?"
date: 2009-12-06
forum: Multimedia Software
---

### Post by sticke4 on 2009-12-06
I am trying to remux my AVI files to MP4 files so that I can play them on my Xbox 360. The AVI files have H264 video codec and MP3 audio codecs, but the Xbox 360 doesn't support h264 in an AVI container. Because it is already in the correct codec, just not the right container, I would think remuxing would be the best way to accomplish playing the videos on my Xbox 360. 

After googling around, I found a few guides and scripts on how to remux MKV files to MP4 but none specifically on how to remux AVI files to MP4.

I did try using avidemux and setting both the video streams and audio streams to copy. The resulting file is very stuttery, as in the video isn't running smoothly and the frames are very jerky, making the video unwatchable.

I also read that one could remux video files to the MP4 container by using ffmpeg or MP4box (gpac). Although, I am unsure what options to use to get my desired effect. If anyone could explain what the different methods to do this, it would be greatly appreciated.

---

### Post by lovinglinux on 2009-12-06
Perhaps you could use mencoder.

Try this:

```
mencoder original.avi -oac copy -ovc copy -o output.mp4
```

This will not re-encode, just save the original audio and video streams onto a mp4 container. I'm not sure if this is enough, because I don't own a XBOX.

> **sticke4 said:**
> After googling around, I found a few guides and scripts on how to remux MKV files to MP4 but none specifically on how to remux AVI files to MP4.

If you know how to do that, than all you have to do is mux the original AVI to a MKV container using MKVMerge GUI, then remux it to mp4.

---

### Post by sticke4 on 2009-12-07
Thank you for the code, it was very helpful. Yet, I think there is another problem that is preventing the file to play on my Xbox 360, that i have only just realized. The Xbox 360 only supports H.264/AVC video codec in an MP4 container, **and** it only supports AAC audio. My video file had MP3 audio, which probably caused some additional problems. 

I would suppose that I would have to extract/dump the Video and Audio; then convert the Audio to AAC; and finally remux all of it to a MP4 container. How would I do this? I am lost in all the ways that one could accomplish this. Also, is this the best way on handling it. Or can ffmpeg or another program convert the Audio without needing to first extract them. Thank you for all your help so far.

---

### Post by lovinglinux on 2009-12-07
> **sticke4 said:**
> Thank you for the code, it was very helpful. Yet, I think there is another problem that is preventing the file to play on my Xbox 360, that i have only just realized. The Xbox 360 only supports H.264/AVC video codec in an MP4 container, **and** it only supports AAC audio. My video file had MP3 audio, which probably caused some additional problems. 

I would suppose that I would have to extract/dump the Video and Audio; then convert the Audio to AAC; and finally remux all of it to a MP4 container. How would I do this? I am lost in all the ways that one could accomplish this. Also, is this the best way on handling it. Or can ffmpeg or another program convert the Audio without needing to first extract them. Thank you for all your help so far.


```
mencoder original.avi -oac lavc -lavcopts acodec=libfaac:abitrate=128 -ovc copy -o output.mp4

```

---

### Post by andrew.46 on 2009-12-08
Hi sticke4,

And the FFmpeg equivalent might be something like:

```
ffmpeg -i original.avi -vcodec copy -sameq -acodec libfaac -ab 128k output.mp4
```

if your copy of FFmpeg has been compiled to include [support for libfaac]("http://ubuntuforums.org/showthread.php?t=1117283")...

Andrew

---

### Post by FakeOutdoorsman on 2009-12-08
> **andrew.46 said:**
> Hi sticke4,

And the FFmpeg equivalent might be something like:

```
ffmpeg -i original.avi -vcodec copy -sameq -acodec libfaac -ab 128k output.mp4
```

if your copy of FFmpeg has been compiled to include [support for libfaac]("http://ubuntuforums.org/showthread.php?t=1117283")...

Andrew

Hi Andrew,

I believe the *-sameq* option is ignored when using *-vcodec copy*, but that's a good thing because *-sameq* is an option that can be used when re-encoding is desired.

---

### Post by andrew.46 on 2009-12-09
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> Hi Andrew,

I believe the *-sameq* option is ignored when using *-vcodec copy*, but that's a good thing because *-sameq* is an option that can be used when re-encoding is desired.

Oops, I was not aware of that, my apologies for giving dodgy advice :-#.

Andrew

---

### Post by h4ppycl0wn on 2009-12-09
Hi,

If you'd prefer a graphical application to do movie encoding I have found Handbrake to be useful and will output H.264/AAC mp4 files. Didn't find a way for it to just copy the video stream though.

[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

I can confirm the .deb package is working on 9.10 ubuntu.

Thanks,
Phil.

---

### Post by FakeOutdoorsman on 2009-12-09
> **andrew.46 said:**
> Hi FakeOutdoorsman,

Oops, I was not aware of that, my apologies for giving dodgy advice :-#.

Andrew

I wouldn't call it dodgy, especially since it didn't change the output at all.  I'm there with you though, I give dodgy advice more often than I would like to.

---


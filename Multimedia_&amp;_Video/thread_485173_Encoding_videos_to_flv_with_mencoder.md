---
title: "Encoding videos to flv with mencoder"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by sparrowkc on 2007-06-26
I've been googling for a while now, and I can't seem to find any discussion on this topic.  

My goal is to get all my videos playing on my wii, so I need to get conversion to flv working.


mencoder -ovc help     gives

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding

---

### Post by Jellyffs on 2007-06-26
Hi,

[http://www.jellykernel.org/index.php?option=com_content&task=view&id=157&Itemid=49](http://www.jellykernel.org/index.php?option=com_content&task=view&id=157&Itemid=49)

;)

---

### Post by sparrowkc on 2007-06-26
I tried using ffmpeg, but I couldn't get it to compile with mp3 support, so the product of what you suggested has no sound.  A description of how to get that working would be great though!

---

### Post by Jellyffs on 2007-06-26
All you need is to have the right packages for mp3 support (have a look at the doc). And you'll have sound.

---

### Post by sparrowkc on 2007-06-26
I used these instructions and I am still having this problem. [https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)

What is the package you are talking about? Do I still need to have a specific compile option, or do I just need to install something with synaptic?

---

### Post by trak87 on 2007-06-26
According to this thread you need to have the win32 codecs installed:

[http://lists.mplayerhq.hu/pipermail/mencoder-users/2007-January/004939.html](http://lists.mplayerhq.hu/pipermail/mencoder-users/2007-January/004939.html)


According to this it's difficult, flv is proprietary and is not a great quality container format, so the author kinda asks what's the point. But he shows it is possible with ffmpeg:

[http://parallaxed.net/article/convert-to-flv-flash-video-with-ffmpeg](http://parallaxed.net/article/convert-to-flv-flash-video-with-ffmpeg)

I mean, nothing on youtube is particularly good quality video...

---

### Post by sparrowkc on 2007-06-26
I checked and I do have the win32 codecs.

---

### Post by Jellyffs on 2007-06-27
flv is proprietary but is still a great container. Youtube videos are poor because the source of the video is poor, and also because Youtube highly compress their video. 

Now, make sure you have these packages:

```
gstreamer0.10-ffmpeg
```
```
gstreamer0.10-fluendo-mp3
```

That should be enough to enable mp3 support.

---


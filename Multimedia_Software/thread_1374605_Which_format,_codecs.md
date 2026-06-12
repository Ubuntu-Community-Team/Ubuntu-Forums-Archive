---
title: "Which format, codecs"
date: 2010-01-07
forum: Multimedia Software
---

### Post by needhelppeeps on 2010-01-07
I have some video I want to edit and send to others. I am using avidemux because most other editors I tried crashed a lot. It's currently in .flv and I no longer have access to the shockwave files. I can play the files fine as .flv, but those with windows I cannot. I tried saving using several different codecs as avi and mpeg files. Sometimes the windows users can't play them at all. Other times they can but the color doesn't look good. On my Linux system, all of these files play without error or poor color.

What are some codecs and containers that should work reliably on both Linux and Windows machines without needing them to install special softwares? I care more about quality than compression.

---

### Post by csaratchand on 2010-01-07
1. Try WinFF (winff in Synaptic Package Manager). It can do many of the things that FFMPEG can do.
2. If you are looking for compatibility with Windows and quality then you must strike a compromise:
a. Try the avi container i.e. choose AVI from WinFF's **Convert To** drop-down menu.
b. In WinFF's **Device Preset** choose **MS Compatible AVI**.
3. Convert your .flv file and check out the results. If there is a problem then get back.

---

### Post by howefield on 2010-01-07
> **csaratchand said:**
> 1. Try WinFF (winff in Synaptic Package Manager). It can do many of the things that FFMPEG can do.

And well it should, seeing as it is a front end for ffmpeg :)

---

### Post by FakeOutdoorsman on 2010-01-07
> **needhelppeeps said:**
> I have some video I want to edit and send to others. I am using avidemux because most other editors I tried crashed a lot. It's currently in .flv and I no longer have access to the shockwave files. I can play the files fine as .flv, but those with windows I cannot. I tried saving using several different codecs as avi and mpeg files. Sometimes the windows users can't play them at all. Other times they can but the color doesn't look good. On my Linux system, all of these files play without error or poor color.

What are some codecs and containers that should work reliably on both Linux and Windows machines without needing them to install special softwares? I care more about quality than compression.

You may not have to re-encode the video and instead may be able to place it into a more suitable container format.  Install FFmpeg.  Then show the output of:
```
ffmpeg -i the_flv_file_that_you_want_to_convert.flv
```
This will output useful information about the contents of the video.

As an alternative solution, you could have the Windows machines install [VLC](http://www.videolan.org/), which, in my opinion, is the best Windows media player and would possibly play the original flv file just fine.

---

### Post by SuperSonic4 on 2010-01-07
I've never had any problem with flv files on Windows unless I'd forgot to install VLC :p

---

### Post by mcduck on 2010-01-07
In my opinion the best video formats considering the support on different platforms, quality, and file size would be either divx/xvid video and mp3 audio in .avi container, or h.264/x.264 video and AAC audio in .mp4 container. The first one is slightly better supported while the later one provides better quality and still works with pretty much every OS and video player.

.flv is pretty crappy format as a video container and isn't really commonly supported format in video player applications and devices. It's best suitable for Internet use, not really for video files you view on your computer.

Of course it would help to know what format your video files are now encoded in, and not just the container you have used... If they are h.264 files then the best option is of course to remux them into .mp4 container to avoid having to re-encode the video. :)

---


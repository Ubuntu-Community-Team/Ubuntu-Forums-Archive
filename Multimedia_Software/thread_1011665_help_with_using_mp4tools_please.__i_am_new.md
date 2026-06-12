---
title: "help with using mp4tools please.  i am new"
date: 2008-12-15
forum: Multimedia Software
---

### Post by chee on 2008-12-15
i am wondering if someone can explain how to use mp4tools.   i installed it and updated the 2 lines in my sources like it says but i have to be honest i really like using linux and it works great for me but i am really not very good at using the terminal and doing anything without synaptics so i am surprised i got this far.

what i want to do is convert some avi files to mp4's and see if i can put them on my Ipod Nano video,  using gtkpod.  i used it for songs successfully but apparently videos must be in mp4 formatt which is where i hit a wall.

any help would be greatly appreciated and i apologize for the pathetic question,  my good friend who set my computer up has moved away so i can't bug him anymore with these questions.  

thank you

---

### Post by prshah on 2008-12-15
> **chee said:**
> 
what i want to do is convert some avi files to mp4's and see if i can put them on my Ipod Nano video,

I don;t know about mp4 tools, but I suggest you use ffmpeg instead. You can install it by [clicking here]("apt://ffmpeg")

To use it, open a terminal (Applications-Accessories-Terminal) then navigate to your directory where the video are stored, and give the command```
ffmpeg -i xxx.avi xxx.mp4
``` where xxx.avi is the name of the avi file and xxx.mp4 is the mp4 file to be created.

You can also force (another) ipod format with the command```
ffmpeg -f ipod -i xxx.avi xxx.mp4
```

Post back if you have difficulties.

---

### Post by eye208 on 2008-12-15
Unfortunately you can't just convert video to .mp4 and expect it to work with the iPod. You have to configure the x264 codec properly to produce a format that is compatible with the iPod.

Avidemux has an iPod preset. Please try this first. If it doesn't work for some reason, I can show you how to do it with MEncoder.

---

### Post by prshah on 2008-12-15
> **eye208 said:**
> You have to configure the x264 codec properly to produce a format that is compatible with the iPod.

ffmpeg produces mp4s' with the H.264 codec; what other "proper" configuration are you suggesting?

```

ffmpeg -formats | grep ipod
FFmpeg version SVN-r16054, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: 
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 6. 1 / 52. 6. 1
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  built on Dec 11 2008 17:58:28, gcc: 4.3.2
[color=red]  E ipod            iPod H.264 MP4 format[/color]

```

---

### Post by eye208 on 2008-12-15
> **prshah said:**
> ffmpeg produces mp4s' with the H.264 codec; what other "proper" configuration are you suggesting?
H.264 playback on the iPod is subject to many restrictions regarding resolution, bitrate, number of macroblocks per frame, number of B-frames, number of reference frames, etc.

x264 is perfectly capable of producing iPod-compatible streams if configured correctly. Some tools (such as Avidemux) have built-in iPod presets for x264. I don't know if ffmpeg has any but I doubt it.

You can read more about it [here](http://forum.handbrake.fr/viewtopic.php?f=7&t=1732).

---

### Post by chee on 2008-12-15
thanks for the posts.  i do really appreciate it.

so i tried ffmpeg the way that was posted (like this exactly : ffmpeg -i faster.avi faster.mp4 and i also tried the other one ffmpeg -f ipod -i faster.avi faster.mp4) and it said that eithe the input or output was in a format that wasn't recognized.
so if i am doing something wrong tell me.  if i have to update something maybe?

i am in the midst of trying avidemux.  i am at work so it might take a bit. 

thank you again.  i do really want to learn this kind of stuff as i really like using linux,  i just don't really know where to start.  any other suggestions are very welcome.

---

### Post by chee on 2008-12-15
BTW do you guys recommend gtkpod?  i have read a bit about ipodlinux but i am still not sure about it.  i don't really know how to install it either,  and i did read the install instructions.  it said something about not being used with newer versions of the ipod.  mine is the newest ipod nano 4gb video.

sorry,  i should do one question at a time.

---

### Post by FakeOutdoorsman on 2008-12-15
> **eye208 said:**
> ...
I don't know if ffmpeg has any but I doubt it.
FFmpeg does have an ipod "preset" as prshah points out, but unfortunately ffmpeg from the repository is too old to include this preset.  You would have to compile a recent ffmpeg yourself to use "-f ipod":
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Compile the latest ffmpeg and x264 from source[/url]

An easier option is to install ffmpeg with the unstripped libraries:
```
sudo apt-get install ffmpeg libavcodec-unstripped-51
```
Then get [WinFF](http://code.google.com/p/winff/wiki/UbuntuInstallation), a GUI for ffmpeg.  WinFF has presets for ipod.

---

### Post by chee on 2008-12-15
so is every mp4 the same?  i mean can i put any mp4 video on my ipod or do i need a certain type.  i'm a little lost here.  i went through the suggested HOWTO: Compile the latest ffmpeg and x264 from source and it seems to be working but i must admit that i was kind of walking blind.  i used the aivdemux and it did create a mp4 file which is fine,  but now i have to figure out how to get the thing on my ipod,  but some else has a thread going about that.  one step at a time.

thanks and all suggestions are always welcome.

---

### Post by eye208 on 2008-12-16
> **chee said:**
> so is every mp4 the same?
Yes and no. MP4 is a common container format for video streams, audio streams, and other data such as subtitles, chapter information etc. It supports all types of MPEG streams and a few others such as AC-3. So the container itself is the same, but its contents can be anything.

> i mean can i put any mp4 video on my ipod or do i need a certain type.
Not only do you need a certain type (i.e. H.264 video + AAC audio) but also particular profiles of these. For example, H.264 video can be anything from low-bandwidth webcam style to high-quality HD. Even lossless H.264 compression is possible. The iPod's capabilities have been improved with each new generation, but even the latest ones support only H.264 baseline 3.0 profile. Of course this makes perfect sense for a battery-powered device with a small display.

The iPod presets of Avidemux and FFmpeg are shortcuts to configure the x264 codec so that it produces iPod-compatible H.264 streams.

---


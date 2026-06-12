---
title: "Stream analog NTSC video through avconv."
date: 2013-02-28
forum: Multimedia Software
---

### Post by tyzoid on 2013-02-28
Hello, everyone.

I'm trying to do a live stream of video from an NTSC output, live video that passes through a DVD player before being sent to my computer. I have a em28xx device, and audio recording works fine. The problem is with the video. Whenever I try and record video, it attempts to record it as if it were PAL.

-Note, this setup cannot be changed because I am trying to stream church service. This requires that I use avconv.

Here is the command I am using:
```
avconv -f video4linux2 -i /dev/video1 -f alsa -i hw:1,0 -ar 44100 output.mov
```

Here is a screenshot:
[ATTACH=CONFIG]239525[/ATTACH]

I can play the video fine using ```
mplayer tv:// -tv norm=NTSC so I know that the device works fine.

I tried to force it into NTSC mode with this command, but it gives me an error.
[code]$ v4l2-ctl -s=ntsc
VIDIOC_S_STD: failed: Invalid argument
```
System specs:
```

$uname -a
Linux Tyler-Linux 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

$lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:qt4-3.1-amd64:qt4-3.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

```

Running on an intel Centrino 2. (HP Dv7 laptop)

---

### Post by tyzoid on 2013-03-02
-bump-
Anyone have any hints? I was hoping to be able to have this done by tomorrow...

---

### Post by tyzoid on 2013-03-03
Ok, so I've found out that there are no video standards supported by my installation of v4l2:
```
$ v4l2-ctl --list-standards
ioctl: VIDIOC_ENUMSTD
```

Anyone know how to add these? I searched through Synaptic and didn't find anything.

---

### Post by FakeOutdoorsman on 2013-03-03
I don't use avconv, but I can help you with ffmpeg. Please show the output of:
```
ffmpeg -f video4linux2 -list_formats all -i /dev/video1
```
Get a [recent static build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) to avoid the rampant avconv bugs.

---

### Post by tyzoid on 2013-03-09
I've fixed the video with ffmpeg, forgot to post back. Now my audio quit :/

I'm trying to capture audio through my em28xx device. alsa is recognizing it (as recorder hw:1,0) and alsamixer shows the device turned up, but no sound comes through...

---


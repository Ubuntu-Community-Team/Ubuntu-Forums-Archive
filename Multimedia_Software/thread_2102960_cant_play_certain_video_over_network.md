---
title: "cant play certain video over network"
date: 2013-01-08
forum: Multimedia Software
---

### Post by youngdaddytc on 2013-01-08
PROBLEM:  certain video files will not play over network BUT WILL PLAY if copied, then pasted to desktop.

OCCURS:  only some video files have this problem.  the files i am having the problem with are using MPEG-4 AAC for audio and H.264 for video in a quicktime container and are in a .mp4 format (according to the audio/video properties of the files.)

HAVE TRIED:  multiple distros, multiple players, and have installed every codec package available through synaptic for each distro.   i have experienced this issue with ubuntu, Kubuntu, linux mint, linux mint xfce, and puppy linux.  i have attempted to use totem player, vlc, gnome player, and all experience this issue.  

OTHER:  only happens on 1 laptop, which is a dell inspiron 1150.  my other laptop which is an hp dv6800 (and runs ubuntu x64) plays them just fine.   the specs of the inspiron 1150 are...

**Processor / Chipset**

 
[LIST]
[*] **CPU**  Intel Celeron 2.6 GHz
[*] **Cache**  L2 cache - 128.0 KB
[*] **Front Side Bus**  400.0 MHz
[*] **Chipset**  Intel 852GMV
[/LIST]
 **Memory**

 
[LIST]
[*] **RAM**  256.0 MB
[*] **Max RAM Supported**  1.0 GB
[*] **Technology**  DDR SDRAM
[*] **Speed**  266.0 MHz
[*] **Slots Qty**  2
[*] **Empty Slots**  1.0
[/LIST]
 **Storage**

 
[LIST]
[*] **Floppy Drive**  None
[*] **Hard Drive**  30.0 GB HDD
[*] **Storage Removable**  None
[*] **Optical Drive**  CD-RW/DVD
[*] **Read Speed**  8x
[*] **Optical Drive (2nd)**  None
[*] **Hard drive type**  Portable
[/LIST]
 **Display**

 
[LIST]
[*] **Max Resolution**  1024 x 768 ( XGA )
[*] **Widescreen**  No
[/LIST]
 **Audio & Video**

 
[LIST]
[*] **Graphics Processor**  Intel Extreme Graphics 2
[*] **Memory Allocation Technology**  Shared video memory (UMA)
[*] **Compliant Standards**  AC '97
[/LIST]


now i know these aren't the best specs, especially that 256 MB of ram.  however keep in mind it does play these files, once copied n pasted onto the desktop.  so why not over the network?  any help would be appreciated.

---

### Post by youngdaddytc on 2013-01-09
bump

---

### Post by FakeOutdoorsman on 2013-01-09
If the overall bitrate of the videos are greater than your bandwidth then playback may suffer although I'm not really an expert or anything when it comes to networking.

A simpler problem may be the location of the "moov" atom in the videos in the MP4 container. This is often located at the end of the file resulting in a requirement for complete download before playback. You can move the moov from the end of the file to the beginning, thus facilitating playback, with ffmpeg, qt-faststart (part of FFmpeg), or MP4Box (part of the gpac package):

**ffmpeg**
```
ffmpeg -i input.mp4 -c copy -map 0 -movflags faststart output.mp4
```

**qt-faststart**
```
qt-faststart input.mp4 output.mp4
```

**MP4Box**
```
MP4Box -add input.mp4 output.mp4
```

Note that my ffmpeg example is for [current ffmpeg from FFmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)--not the [fake junk](http://stackoverflow.com/a/9477756/1109017) in the repository. Also, I didn't test it, so I'm not exactly sure if "-movflags faststart" works with stream copying.

---

### Post by youngdaddytc on 2013-01-12
thank you for your suggestion, i will try this as soon as time allows then post back my results.

---


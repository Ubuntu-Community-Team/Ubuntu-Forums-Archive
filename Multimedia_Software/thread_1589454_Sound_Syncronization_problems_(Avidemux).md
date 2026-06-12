---
title: "Sound Syncronization problems (Avidemux)"
date: 2010-10-06
forum: Multimedia Software
---

### Post by R3M3 on 2010-10-06
I'm trying to prepare some .mpg (audio & video) files for transfer to a DVD. Currently I'm trying to use Avidemux to do the pre-processing, and DVD-Styler to do the actual .iso building.

From what I've read, I'm doing the following to prepare the files:
* Trim unwanted parts from the front and back of the video
* Resample video framerate from 59.96 to 29.97 (I'm in the US)
* Crop and resize video to 720x480
* Convert/resample audio to 48kHz Stereo
* Save video in DVD (lavc) format (two pass, video size), and audio in MP2 (Twolame) format in an MPEG PS A+V container file.

I'm running into a problem where the output file has a rather severe and noticeable delay between the video and the audio. Avidemux reports a 0 ms delay on the input file (from the Audio->Main dropdown box), which matches the settings I used for transcoding. I've tried passing the input file through Project X to clean it up, prior to using Avidemux, but that doesn't seem to work.

Anyone have any suggestions on how to fix the audio/video desync?

---

### Post by R3M3 on 2010-11-01
After quite a lot of trial and error, I think I figured it out.

Apparently, I was asking too much of Avidemux on one go. If I split the job into multiple parts, it seems to do much better. Specifically, I did a first pass with the cutpoints (trimming excess video form the beginning and end) but without transcoding. The second pass on the new, shortened file (which has a small but non-zero sound offset) does the transcoding. This two-pass process seems to give files without the noticeable sound shift I was seeing earlier.

---

### Post by R3M3 on 2010-11-02
... or maybe not.

The first couple appeared to be good, but then others seemed to be fine near the beginning, but had audio/video desync getting progressively worse towards the end. I've now also had some where the audio/video sync was completely broken even at the start. 

So the two-step process seems to fix the issue on some files, on others it's still a mess.

---

### Post by xc3RnbFO8P on 2010-11-02
Did you try in tools > Rebuild Frames ( I & B )

---

### Post by Ragnar! on 2010-11-06
You can also get an app called mediainfo and run it on your source file. It will tell you lots of stuff about your media. One of those things will be frame rate. Make sure that avidemux is set to the same frame-rate as your source file (video-frame rate on the toolbar). this fixed my sync problem as my video was at 24.976 yet avidemux had set it to 29.xxx (forget exactly). This completely solved my sync issue.

---


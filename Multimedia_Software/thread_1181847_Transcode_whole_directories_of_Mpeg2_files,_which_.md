---
title: "Transcode whole directories of Mpeg2 files, which program?"
date: 2009-06-08
forum: Multimedia Software
---

### Post by Col-1023 on 2009-06-08
I have hundreds of music videos and tv shows in the mpeg2-ac3 and mpeg2-mp2 formats and I want to convet them to x264-mkv, while keeping the audio as the original.

Avidemux can convert files but you need to deal with them one at a time, but I just want to put the files in a single directory and convert them all to the same x264.


I would like to be able to tweak the x264 settings as well, and most of the videos are interlaced.

Any help appreciated,

TIA.

---

### Post by Arup on 2009-06-08
Have you tried Handbrake or WinFF?

---

### Post by Col-1023 on 2009-06-08
I've heard of handbreak, but know little about it other than it's a command line package, is it very easy for some who is used to avidemux and a gui to use?

I don't really know anything about winff, so I'll check it out too.



Thanks alot for your help Arup.

---

### Post by reeseslover531 on 2009-06-08
If you are just a little familiar with the command line, mencoder is easy to script and is a wonderful encoder.  You can check out a overview of how to use it at the [wiki ]("https://help.ubuntu.com/community/MEncoder")page

---

### Post by mastermindg on 2009-06-08
Yes, mencoder is the way to go. You can add actions for both Gnome and KDE that can encode whole directories.

---

### Post by FakeOutdoorsman on 2009-06-08
This can be easily done with FFmpeg, the libx264 presets, and *find*.  If you have Jaunty Jackalope you're in luck because FFmpeg from the repository already has the presets, but you just have to enable them:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Users of older Ubuntu versions can still use the presets, but they will have to compile FFmpeg and x264:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

Now you can use the find command to do your bidding and encode everything all at once:

[Linux Basics: A gentle introduction to 'find'](http://ubuntuforums.org/showthread.php?t=1128937)

An untested sample command that will encode all *.mpg files in the */home/foo/Desktop/video* directory:
```
find ~/Desktop/videos -name '*.mpg' -type f -exec ffmpeg -i '{}' -acodec copy -vcodec libx264 -vpre hq -deinterlace -threads 0 -crf 24 '{}'.mkv \;
```
I added the optional *-deinterlace* parameter.  The *-crf* option controls the quality.  A lower value is a higher quality.  A sane range is 18-30.

---

### Post by Col-1023 on 2009-06-10
Thanks fakeoutdoorsman for your pointer to the FIND command, if my experience with the new handbrake doesn't work out, then I'll give ffmpeg a try, though I'll need to learn how to set x264 options by the command line.

I've had another look at handbrake (v9.3) and it now comes with a gui for linux.

It seems to do what I want, but I have some questions.

1 - The de-Comb option means it will deinterlace the video if necessary.  I have been worried about using deinterlacers since if you get the settings wrong (top field or bottom first, etc), the video can be much worse than leaving it interlaced, decomb has no settings other than enabling it, so is decomb safe to use in all interlaced videos (PAL 720x576 @ 25 and 1440X1088 @ 25 fps)?

2 - The audio options allow for ac-3 pass-thru (the perfect option for me in most cases since it won't touch the ac3 stream), but some of my videos have mp2 audio (256k or 192k), and there is no audio-copy option, so should I just encode this mp2 audio as say mp3 256k, vorbis 192k or aac 160k, and will re-encoding this audio have any noticeable bad effects.

3 - Is the auto-crop conservitave or is it too agressive, I've noticed with avidemux that autocrop can overcrop some dark areas of a video, so I set my own crop points, should I turn auto-crop off?

4 - Does the MKV container care what audio codec is used, since I've read that mp4 only likes aac as the audio stream?

Any help appreciated.

---

### Post by reeseslover531 on 2009-06-10
I am not sure about all the questions, but here is what I can answer. 

2. There won't be too much of a degradation of audio quality of you re-encode and it might just make things easier if you re-encode to codec such as vorbis or mp3.

3. I find the auto-cropping in Handbrake to be VERY good, I think they make a point to stay on the safe side so that they don't crop dark parts of the video.

4. MKV can accept a staggering amount of audio codec, so I don't think you should worry, especially if you end up re-encoding.

---

### Post by andrew.46 on 2009-06-10
Hi Col,

> **Col-1023 said:**
> Thanks fakeoutdoorsman for your pointer to the FIND command, if my experience with the new handbrake doesn't work out, then I'll give ffmpeg a try, though I'll need to learn how to set x264 options by the command line.

This was a problem that I had myself that has for the most part been resolved with the use of FFmpeg presets which FakeOutdoorsman has demonstrated with:

```
-vcodec libx264 *-vpre hq*
```

so even a slow old man like me can transcode with x264 quite readily :-).

> but I have some questions.[...]
4 - Does the MKV container care what audio codec is used, since I've read that mp4 only likes aac as the audio stream?

I have snipped away the questions I cannot answer :-). As reeseslover531 has mentioned the matroska container is the least limited of all the containers. Have a look at this page which gives a decent comparison of the different containers and the codecs they can carry:

Comparison of container formats
[http://en.wikipedia.org/wiki/Comparison_of_container_formats](http://en.wikipedia.org/wiki/Comparison_of_container_formats)

All the best,

Andrew

---

### Post by Col-1023 on 2009-06-11
Thanks Reeselover531 and Andrew.46 for your replies.

I'm trying out handbrake now, and so the the auto-crop REALLY ROCKS!!

You have to be careful if the video uses different borders throughout, but most videos don't, so the average it uses is great.

The de-comb feature seems to work, but my videos are very noisy (visual.

I've decided to use vorbis @ 160kbs stereo for the audio, and it works well for the old shows I'm encoding (Tom Baker Dr Whos).

I haven't noticed any sync problems with the few encodes I've don so far, but I've read that vorbis is variable bitrate, so will this cause sync problems as compared to ac3?

---


---
title: "Suitable image format for burning mov files on a DVD."
date: 2013-10-09
forum: Multimedia Software
---

### Post by arroy_0209 on 2013-10-09
I am trying to use brasero in ubuntu 12.04  to burn a .mov file on a DVD so as to get a dvd which can be run on a dvd-player. It is to be noted that my dvd-player can run CD, DVD, MP3, sVCD, DVD+-R/RW, WMA, JPEG. This however does not mean that if a .mov file is burned on a CD then it can be run on the pleyer. It fails to run as I have seen already.

Thus I need to burn the .mov file on a DVD. This is the first time I am using brasero and have some confusions which are not cleared by consulting google search results. 
1. What should the disc image type that Brasero will produce? options are: SVCD image/video DVD image/VCD image. Please explain briefly.

2.What should be video format? options: native/PAL/SECAM/NTSC.

3. What should be aspect ratio? 4:3 or 16:9?

---

### Post by qyot27 on 2013-10-10
Burning it to a DVD as data will fail just like burning it to CD as data fails.  It needs to be authored into a proper video DVD, which means it'll cease to be a .mov file with whatever video format (likely H.264) it contains.  The video stream has to be converted to MPEG-2, the audio stream has to be converted to either MP2 or AC3, and then those constituent parts muxed back together and specially processed so that the proper DVD filesystem structure is generated.

1. Video DVD image; SVCD and VCD are for CD media only, not DVDs (they also have different format restrictions in regard to resolution and for VCDs, using MPEG-1 instead of MPEG-2).

2. This depends on the region of the world you're in.  NTSC is North America and Japan ([and parts of South America, South Korea, Myanmar, and the Phillipines, apparently](http://en.wikipedia.org/wiki/File:PAL-NTSC-SECAM.svg)), PAL is pretty much everywhere else.  SECAM is an analog format that has nothing to do with digital representation - for digital purposes, these regions also use PAL.  On a more technical level, 'NTSC' refers to 29.97* frames per second at a resolution of 720x480 (or 704x480, 352x480, 320x240, and 352x240), 'PAL' refers to 25 frames per second at a resolution of 720x576 (or 704x576, 352x576, 320x288, or 352x288).  Technically, since the advent of digital broadcast, NTSC and PAL are not their names (actual NTSC and PAL were analog systems like SECAM), but it's a shorthand habit.

*or 23.976 frames per second for film, treated with telecining so that it's seen by the television as 29.97.  This can be achieved by either hard or soft telecining (also known as 3:2 pulldown).  Special processing allows for special cases of telecining (both hard and soft) to allow other fps values to be used with either system, but the resolution is non-negotiable.

3. If the videos are nearly square, then use 4:3.  If they're 'widescreen', use 16:9.  Depending on exactly what type of widescreen aspect ratio they have, there may need to be borders applied to them (16:9 itself does not; 2.35:1/2.39:1, on the other hand, does).  It's down to the math; divide the width of the video by the height, and compare against the results of 4/3 (1.3 repeating) or 16/9 (1.7 repeating 8).  The 2.35/2.39 case is already telling you that the result of width/height should be 2.35 or 2.39 - you'll encounter this on video with a resolution of say, 1920x800 instead of 1920x1080.  For proper DVD authoring, 2.35/2.39 needs to be letterboxed to fit in a 16:9 frame, so you'd add black borders to the top and bottom.

I would recommend using a dedicated DVD authoring program to prepare the files first.  I don't know how well Brasero treats this scenario, and if you've got to deal with files with several different aspect ratios, then DVD authoring software will give you more control.  Unfortunately, I can't give any recommendations for DVD authoring programs on Linux (except maybe [Bombono DVD](http://www.bombono.org/cgi-bin/wiki/Install_In_Ubuntu)), since my DVD workflow is Windows-based.




As a side note, if the .mov file contains H.264 video and AAC audio (or possibly AC3, MP2, or MP3), there are many Blu-ray players which could handle it if you just remux* the file as either MP4 or Matroska (aka MKV).  These also generally have the ability to play the files from a flash drive too.

*for example,
```
ffmpeg -i input.mov -vcodec copy -acodec copy output.mp4
```
or
```
mkvmerge -o output.mkv input.mov
```

---

### Post by Dean28 on 2013-10-10
> **arroy_0209 said:**
> I am trying to use brasero in ubuntu 12.04  to burn a .mov file on a DVD so as to get a dvd which can be run on a dvd-player. It is to be noted that my dvd-player can run CD, DVD, MP3, sVCD, DVD+-R/RW, WMA, JPEG. This however does not mean that if a .mov file is burned on a CD then it can be run on the pleyer. It fails to run as I have seen already.

Thus I need to burn the .mov file on a DVD. This is the first time I am using brasero and have some confusions which are not cleared by consulting google search results. 
1. What should the disc image type that Brasero will produce? options are: SVCD image/video DVD image/VCD image. Please explain briefly.

2.What should be video format? options: native/PAL/SECAM/NTSC.

3. What should be aspect ratio? 4:3 or 16:9?

1. ```
sudo apt-get install devede
```
2. PAL = Europe NTSC = America
3. 4:3 = Full screen 16:9 = Widescreen

---


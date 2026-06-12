---
title: "Help with Video Processing - Overlay Text, Fade In/Out, Stretch, Concatenate"
date: 2010-03-17
forum: Multimedia Software
---

### Post by BrandonMintern on 2010-03-17
Hi, I'm pretty new to video processing so please bear with me. I am looking for a solution that will allow me to take the following parts:

[LIST]
[*]constant 15-second audio clip
[*]constant 11-second video clip (no audio)
[*]given text file
[*]given video file of arbitrary length
[*]constant 3-second video clip (no audio)
[/LIST]

and combine them into a single final video. The resulting video is


<15-second audio clip>
[LIST]
[*]11-second video clip with text file overlaid on it, stretched (maintaining aspect ratio) to the height of the video file, pausing on the final frame
[*]the final frame fades to black over a period of 2 seconds
[*]the first frame of the video file fades from black over a period of 2 seconds
[/LIST]
</15-second audio clip>

then the entire video plays with its own audio, freezing on the last frame

<no audio>
[LIST]
[*]the last frame fades to black
[*]the first frame of the 3-second clip fades from black
[*]the 3-second clip plays
[/LIST]
</no audio>

Now I'm sure all this is possible to do via the command line, but I'm at a bit of a loss on where to start. I've been messing around with ffmpeg (installed using the process from [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)), but most of the information I'm finding is for the vhooks interface which is no longer available. So I tried to look into libavfilter, but apparently the HOWTO above does not include libavfilter.

Basically, I need to be able to:
[LIST]
[*]overlay given text using a desired font/color/size on a video clip at a desired y position, centered horizontally
[*]stretch the video clip to be the same height as the video file while maintaining aspect ratio
[*]grab the last frame of one video and the first of another
[*]fade those frames to/from black
[*]combine all this into a single video stream
[*]add the audio clip to this 15-second stream (audio should fade out over the last 4 seconds, but I can probably handle that before this process)
[/LIST]

This will result in one video file (in an uncompressed format?). Obviously the end sequence would have similar requirements, but they are all covered in the intro so I won't specify them explicitly. So then I will have 3 separate videos -- generated intro, video file, generated outro -- that will need combined together.

So... Is ffmpeg+libavfilter the best tool for this sort of thing? If not, can someone suggest a better tool? If it is the right tool, can anyone point me to a resource for including libavfilter in the ffmpeg installation? How can libavfilter work with multiple input files at once?

Thanks a lot for any help you can offer. I'd like to clarify that I'm not asking anyone to spell anything out for me, just offer some links and suggestions. I'm trying to be as explicit as possible so that it's clear what I'm trying to do.

The point is to write a program (or script, or whatever) that accepts a video and a text file and automatically creates what I described above using already-determined intro/outro clips and audio.

Note: One final idea I had... the intro clip is 800x600. Would it be easier to create an 800x600 image using ImageMagick and then overlay that on the intro clip as opposed to using ffmpeg to overlay text?

Another Note: Avisynth is unfortunately not an option. This is going to be on a webhost and I will need to be able to upload static binaries to perform the processing, so WINE+Avisynth is pretty much out of the question.

---

### Post by BrandonMintern on 2010-03-24
Since no one seems to have answers to this, I will be trying to figure it out on my own and answering my questions as I go along.

1. We need to install ffmpeg with libavfilter. For that I have written [**_HOWTO: Install the latest FFmpeg with x264 and libavfilter_**](http://ubuntuforums.org/showthread.php?t=1438052)

2. To grab the first frame of a video:
```
ffmpeg -vframes 1 -i <video input> <image output>
```
<image output> should probably end in .jpg

3. To grab the last frame of a video, I wrote a little program that I called "get-last-frame":
```
#!/bin/sh

FFMPEG="ffmpeg"
video=$1
image_name=$2

duration=`$FFMPEG -i $video 2>&1 | \
    grep Duration | \
    sed 's/.*Duration:\s*\([:0-9.]\+\).*/\1/' | \
    awk -F: '{print ($1 * 3600 + $2 * 60 + $3 - 0.01)}')`

$FFMPEG -vframes 1 -ss $duration -i $video $image_name
```
To run it:
```
./get-last-frame <video input> <image output>
```

I will edit this post as I proceed with the requirements. If you have any tips on anything that I haven't indicated yet, I would appreciate them.

---

### Post by progone on 2010-06-30
This is interesting.  :guitar:

I want to convert a wmv incoming stream into an outgoing mov or FLV stream on a website (HTML5).

Do you know where I begin?  Any hints?


thank you

---


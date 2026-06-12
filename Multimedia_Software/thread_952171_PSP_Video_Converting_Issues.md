---
title: "PSP Video Converting Issues"
date: 2008-10-18
forum: Multimedia Software
---

### Post by seuzy13 on 2008-10-18
](*,)](*,)](*,)

I have tried pspvc, avidemux, winff, ppvc, and a number of psp converting scripts. With all of these I have encountered problems. The most common is that the video will encode well and be playable, but when I move it to my PSP it is "unsupported data" even though I used the correct preset and saved it to the correct folder with the correct name. What could I possibly be overlooking. Every time I try to convert videos to PSP on Linux I get very frustrated. On Windows, it was always a relatively simple process in comparison. This shouldn't be the case!

Help, please?

---

### Post by crossy on 2008-11-15
I realise that it's not helpful, but I've got exactly the same problem. Tried local build of ffmpeg, Handbrake etc and I get the same problem as you - the file converts, transfers okay, and then I get "Unsupported Data" on the PSP. :mad:

What makes it worse is the ****ing thing can actually tell that it's video file etc - just won't play it.

I'm kinda happy that you've got the same issue - at least it means that it's not something I've done wrong. If I get a solution I'll let you know - better still, if someone out there in penguin-land knows, then that'd be cool.

Oh, and I'm running 64bit Hardy.

Bob

---

### Post by seuzy13 on 2008-11-15
Well, a few times since my post I've been able to get it working using the PSP [H.264] preset on avidemux, but it's hit or miss at best. Have you tried using that?

Converting to PSP format can be really frustrating in that the PSP is so specific about it's restrictions and just isn't very flexible in the formats you can use. I think there could be so much more Linux could do with this!

---

### Post by AATLEMIDRM on 2008-11-17
I'm having the same issue, but I think that, at least for me, it's specific to original video files of the .avi type. At least, I've had two sucessful conversions so far, one of type .mkv and one of .mov.

I'm using ffmpeg and x264 as described in this thread: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095). My initial suspicion is that there's a compile-time option that's missing in those instructions.

I'll try to investigate more, but if anyone more knowledgable wants to weigh in, that would be great too.

Paul

---

### Post by FakeOutdoorsman on 2008-11-17
FFmpeg FAQ 3.14 [How do I encode videos which play on the PSP?]("http://ffmpeg.mplayerhq.hu/faq.html#SEC26")

---

### Post by AATLEMIDRM on 2008-11-17
Yeah, that's the command that I'm using. It's not working for avi files.

Paul

---

### Post by AATLEMIDRM on 2008-11-17
Wait, I've been trying a two pass. Let me try the one pass command they list and see what happens.

Paul

---

### Post by FakeOutdoorsman on 2008-11-17
> **AATLEMIDRM said:**
> Yeah, that's the command that I'm using. It's not working for avi files.

Paul
Is ffmpeg giving you an error, or is it just not playing in the PSP?  If it is ffmpeg, paste your ffmpeg command and the full ffmpeg response.

---

### Post by AATLEMIDRM on 2008-11-17
Apologies.

I know that I've based what I'm using on a few sites, including that one. I thought that I had used that one as the working command, but no.

OK, here's what I've used:

```
ffmpeg -y -i "<input file>" -title "<title>" -acodec libfaac -ab 128kb -ac 2 -ar 48000 -vcodec libx264 -level 21 -b 640kb -coder 1 -f psp -flags +loop -trellis 2 -partitions +parti4x4+parti8x8+partp4x4+partp8x8+partb8x8 -g 250 -s 480x272 -pass 1 -passlogfile crapola /dev/null

ffmpeg -y -i "<input file>" -title "<title>" -acodec libfaac -ab 128kb -ac 2 -ar 48000 -vcodec libx264 -level 21 -b 640kb -coder 1 -f psp -flags +loop -trellis 2 -partitions +parti4x4+parti8x8+partp4x4+partp8x8+partb8x8 -g 250 -s 480x272 -pass 2 -passlogfile crapola MAQ10001.mp4
```

Before anyone asks or comments,

a) It's worked for .mvk and .mov files as the input file, just not avi's. And the input file is the full path (hence the quotes).
b) I believe that the -y in the second command was part of the testing process, and is not properly needed so long as the first command dumps to /dev/null.
c) The audio commands in the first command are necessary because of the psp output.

ffmpeg -version dumps the following:

> FFmpeg version SVN-r15865, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 3. 0 / 52. 3. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Nov 17 2008 15:13:22, gcc: 4.3.2
FFmpeg SVN-r15865
libavutil     49.12. 0 / 49.12. 0
libavcodec    52. 3. 0 / 52. 3. 0
libavformat   52.23. 1 / 52.23. 1
libavdevice   52. 1. 0 / 52. 1. 0
libpostproc   51. 2. 0 / 51. 2. 0

I'm trying again using only the command from the ffmpeg faq (single pass) and seeing if that will work. I'll post when I know. Maybe I'm just being too ambitious. :)

Paul

---

### Post by AATLEMIDRM on 2008-11-18
I tried with just the ffmpeg FAQ command. No joy.

Paul

---

### Post by Purple_Potato on 2008-11-22
First compile x264 and FFMPEG from source, there's an excellent tutorial on how to on the forums. When running the ./configure for FFMPEG, be sure to add "--enable-nonfree" as well. This is the script I've found to run all the time after that. Its pieced together from all over the net, and parts are likely redundant, but it works and I'm scared to change it. (BTW, I'm using 2 days ago's SVN) It includes some references for myself at the end. Copy and paste the command into the console.

```
-----------------------------------------------------------
HERE IS MY FINALLY WORKING PSP VIDEO CONVERSION COMMAND!!
-----------------------------------------------------------

mencoder -ofps 30000/1001 -af volume=5:lavcresample=24000 -vf harddup -of lavf \
    -oac faac -faacopts br=128:mpeg=4:object=2:raw -channels 2 -srate 44100 \
    -ovc x264 -x264encopts bitrate=800:global_header:partitions=all:trellis=1:level_idc=30 \
    -of lavf -lavfopts format=psp \
    Noir_Cropped.avi -o output.mp4


--------------
EXPLAINATION
--------------

Encodes sound into the AAC embedded MP4 audio format with FAAC
AAC audio is 128kbs, stereo, sampled at 44100 a second, and boosted 6db

Encodes video into the superior, compressed x264 format, readable by the PSP
Video bitrate is 800kbs, and scales video while keeping ratios intact

Note to self: Before converting the video, you have to be sure that both width and height of the input video are multiples of 16. If they are not, then in command line try:

mplayer <Input.avi> -vf cropdetect

Take the output crop settings and use them in the command:

mencoder -vf harddup,crop=x:y:<x_crop>:<y_crop> -oac copy -ovc copy  <Input.avi> -o <Input_Cropped.avi>

By now your video size should be divisible by 16, and you should be able to encode it for PSP with mencoder! Have fun!

VERDICT:
Works very well! I love you mencoder!



=======================================
PERTINENT INFO FROM THE MENCODER FAQ:
=======================================


13.3.6. Example

So, you have just bought your shiny new copy of Harry Potter and the Chamber of Secrets (widescreen edition, of course), and you want to rip this DVD so that you can add it to your Home Theatre PC. This is a region 1 DVD, so it is NTSC. The example below will still apply to PAL, except you will omit -ofps 24000/1001 (because the output framerate is the same as the input framerate), and of course the crop dimensions will be different.

After running mplayer dvd://1, we follow the process detailed in the section How to deal with telecine and interlacing in NTSC DVDs and discover that it is 24000/1001 fps progressive video, which means that we need not use an inverse telecine filter, such as pullup or filmdint.

Next, we want to determine the appropriate crop rectangle, so we use the cropdetect filter:

mplayer dvd://1 -vf cropdetect

Make sure you seek to a fully filled frame (such as a bright scene, past the opening credits and logos), and you will see in MPlayer's console output:

crop area: X: 0..719  Y: 57..419  (-vf crop=720:362:0:58)

We then play the movie back with this filter to test its correctness:

mplayer dvd://1 -vf crop=720:362:0:58

And we see that it looks perfectly fine. Next, we ensure the width and height are a multiple of 16. The width is fine, however the height is not. Since we did not fail 7th grade math, we know that the nearest multiple of 16 lower than 362 is 352.

We could just use crop=720:352:0:58, but it would be nice to take a little off the top and a little off the bottom so that we retain the center. We have shrunk the height by 10 pixels, but we do not want to increase the y-offset by 5-pixels since that is an odd number and will adversely affect quality. Instead, we will increase the y-offset by 4 pixels:

mplayer dvd://1 -vf crop=720:352:0:62

Another reason to shave pixels from both the top and the bottom is that we ensure we have eliminated any half-black pixels if they exist. Note that if your video is telecined, make sure the pullup filter (or whichever inverse telecine filter you decide to use) appears in the filter chain before you crop. If it is interlaced, deinterlace before cropping. (If you choose to preserve the interlaced video, then make sure your vertical crop offset is a multiple of 4.)

If you are really concerned about losing those 10 pixels, you might prefer instead to scale the dimensions down to the nearest multiple of 16. The filter chain would look like:

-vf crop=720:362:0:58,scale=720:352

------------------------------------------------------------------------------------------------

12.6. Rescaling movies

Often the need to resize movie images emerges. The reasons can be many: decreasing file size, network bandwidth, etc. Most people even do rescaling when converting DVDs or SVCDs to DivX AVI. If you wish to rescale, read the Preserving aspect ratio section.

The scaling process is handled by the scale video filter: -vf scale=width:height. Its quality can be set with the -sws option. If it is not specified, MEncoder will use 2: bicubic.

Usage:

mencoder input.mpg -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell \
    -vf scale=640:480 -o output.avi


---------------------------------------------------------------------------------------------------

12.10. Preserving aspect ratio

DVDs and SVCDs (i.e. MPEG-1/2) files contain an aspect ratio value, which describes how the player should scale the video stream, so humans will not have egg heads (ex.: 480x480 + 4:3 = 640x480). However when encoding to AVI (DivX) files, you have to be aware that AVI headers do not store this value. Rescaling the movie is disgusting and time consuming, there has to be a better way!

There is

MPEG-4 has a unique feature: the video stream can contain its needed aspect ratio. Yes, just like MPEG-1/2 (DVD, SVCD) and H.263 files. Regretfully, there are few video players apart from MPlayer that support this MPEG-4 attribute.

This feature can be used only with libavcodec'iting... (error parsing command line)
troy@troy-desktop:~$ mencoder -vf harddup,autocrop     -oac COPY     -ovc COPY     Noir01.avi -o Nir_Cropped.avi
s mpeg4 codec. Keep in mind: although MPlayer will correctly play the created file, other players may use the wrong aspect ratio.

You seriously should crop the black bands over and below the movie image. See the man page for the usage of the cropdetect and crop filters.

Usage

mencoder sample-svcd.mpg -vf crop=714:548:0:14 -oac copy -ovc lavc \
    -lavcopts vcodec=mpeg4:mbd=2:trell:autoaspect -o output.avi12.10. Preserving aspect ratio


======================================================================================================

```

---


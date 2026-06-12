---
title: "Editing .mkv files and VLC"
date: 2014-02-16
forum: Multimedia Software
---

### Post by VMC on 2014-02-16
> **timsdeepsky said:**
> ....
```
ffmpeg -ss 00:00:12.00 -i input.foo -acodec copy -vcodec copy -t 120 output.foo
```
I open a terminal in the folder the video is in....Then i use this ffmpeg code to cut and copy part of the video....
The 12 is how many seconds in to start grabbing the video....The 120 is how many seconds in to stop grabbing video....

> **FakeOutdoorsman said:**
> You don't need to install it. It's just a binary that you can execute. The commands I provided earlier in this thread should download the latest build and extract the archive. Then you can run it:
```
./ffmpeg -i input output
```
or use the full path:
```
/home/typos1/ffmpeg -i input output
```

If you want to include it into your PATH (I haven't tested this in a recent Ubuntu):
```

mkdir ~/bin
mv ~/ffmpeg ~/bin
. ~/.profile
```

Now the binary will be executed by simply entering "ffmpeg" in your console.  Since this topic is marked solved, I'd like to add a strange behavior I encountered. Hopefully I don't have to start a new topic, since the players already answering questions may have a solution at hand.
Also thanks for the tips both of you and others have provided.

Using VLC as a timer. I found my mkv file I needed to edit out was from the start to 4 minutes and 15 seconds. So I use the following:
```
./ffmpeg -ss 257 -i infile.m4v -acodec copy -vcodec copy outfile.mkv
```

Using VLC again to view by edited out file, it left several seconds on from where I wanted it. BUT VLC didn't start showing the timer again until the exact same time that ffmpeg cut?! In other words, the video started say 253 seconds from the orignal, but VLC didn't start showing the timer again until 257 seconds.

---

### Post by varunendra on 2014-02-16
For splitting .mkv files, I prefer mkvmerge gui (apt-get install mkvtoolnix-gui), although you can also use "mkvmerge" command. For example -
```
mkvmerge -o outputfile.mkv --split 257s inputfile.mkv
```

And since no transcoding is involved, the splitting occurs at KeyFrames (after the specified time), which means the splitting point will usually be a few seconds/milliseconds 'Off' from what you originally specified.

I have no experience with ffmpeg or other command line tools, but I believe any tool that does not involve transcoding will behave exactly the same way (or will be prone to serious errors).

---

### Post by Bucky Ball on 2014-02-16
*Post moved to own thread.*

The title of the other thread had nothing to do with your issues. You increase your chances of getting support by posting new threads with descriptive titles in the appropriate area of the forum rather than tagging onto someone else's thread 26+ posts deep and with a title that is unrelated to your issue.

You can change the thread title here for the next half an hour by editing the first post and 'Go Advanced'. Good luck.

---

### Post by varunendra on 2014-02-16
> **Bucky Ball said:**
> You increase your chances of getting support by posting new threads with descriptive titles in the appropriate area of the forum

+1

(by the way, posting not for the above +1, but to make the thread 'Appear' in my search results. Just did a fresh search, and it did not appear there - old forum bug :()

---

### Post by Bucky Ball on 2014-02-16
Sorry about that. Odd. I'll look into it. ;)

---

### Post by VMC on 2014-02-16
> **varunendra said:**
> For splitting .mkv files, I prefer mkvmerge gui (apt-get install mkvtoolnix-gui), although you can also use "mkvmerge" command. For example -
```
mkvmerge -o outputfile.mkv --split 257s inputfile.mkv
```

And since no transcoding is involved, the splitting occurs at KeyFrames (after the specified time), which means the splitting point will usually be a few seconds/milliseconds 'Off' from what you originally specified.

I have no experience with ffmpeg or other command line tools, but I believe any tool that does not involve transcoding will behave exactly the same way (or will be prone to serious errors).
ffmpeg works perfectly and fast. I might try mkvmerge later though. Thanks for the info. I did find this interesting on the ffmpeg link:
> [COLOR=#202020][FONT=Times New Roman]**‘**[/FONT][/COLOR]-ss position (*input/output*)[COLOR=#202020][FONT=Times New Roman][B]’
[/B][/FONT][/COLOR][COLOR=#202020][FONT=Times New Roman]When used as an input option (before [/FONT][/COLOR]-i[COLOR=#202020][FONT=Times New Roman]), seeks in this input file to [/FONT][/COLOR]position[COLOR=#202020][FONT=Times New Roman]. ***Note that in most formats it is not possible to seek exactly***, so [/FONT][/COLOR]ffmpeg[COLOR=#202020][FONT=Times New Roman]will seek to the closest seek point before [/FONT][/COLOR]position[COLOR=#202020][FONT=Times New Roman]. When transcoding and ‘[/FONT][/COLOR]-accurate_seek[COLOR=#202020][FONT=Times New Roman]’ is enabled (the default), this extra segment between the seek point and [/FONT][/COLOR]position[COLOR=#202020][FONT=Times New Roman] will be decoded and discarded. When doing stream copy or when ‘[/FONT][/COLOR]-noaccurate_seek[COLOR=#202020][FONT=Times New Roman]’ is used, it will be preserved.[/FONT][/COLOR]( Italics&bold are mine)

---

### Post by FakeOutdoorsman on 2014-02-17
> **VMC said:**
> Using VLC again to view by edited out file, it left several seconds on from where I wanted it. BUT VLC didn't start showing the timer again until the exact same time that ffmpeg cut?! In other words, the video started say 253 seconds from the orignal, but VLC didn't start showing the timer again until 257 seconds.

Try:
```
./ffmpeg -i infile.m4v -ss 257 -codec copy outfile.mkv
```

---

### Post by VMC on 2014-02-17
> **FakeOutdoorsman said:**
> Try:
```
./ffmpeg -i infile.m4v -ss 257 -codec copy outfile.mkv
```
Thanks, but I got these errors:
```
**$ ffmpeg -i S4e1.m4v -ss 257 -codec copy output.mkv**
ffmpeg version N-60675-g8fe1076 Copyright (c) 2000-2014 the FFmpeg developers
  built on Feb 16 2014 05:45:47 with gcc 4.6 (Debian 4.6.3-1)
  configuration: --prefix=/root/ffmpeg-static/64bit --extra-cflags='-I/root/ffmpeg-static/64bit/include -static' --extra-ldflags='-L/root/ffmpeg-static/64bit/lib -static' --extra-libs='-lxml2 -lexpat -lfreetype' --enable-static --disable-shared --disable-ffserver --disable-doc --enable-bzlib --enable-zlib --enable-postproc --enable-runtime-cpudetect --enable-libx264 --enable-gpl --enable-libtheora --enable-libvorbis --enable-libmp3lame --enable-gray --enable-libass --enable-libfreetype --enable-libopenjpeg --enable-libspeex --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-version3 --enable-libvpx
  libavutil      52. 64.100 / 52. 64.100
  libavcodec     55. 52.102 / 55. 52.102
  libavformat    55. 32.101 / 55. 32.101
  libavdevice    55.  9.101 / 55.  9.101
  libavfilter     4.  1.102 /  4.  1.102
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'S4e1.m4v':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    creation_time   : 2012-02-21 02:30:55
    encoder         : HandBrake 4458svn 2012022001
  Duration: 00:53:02.64, start: 0.000000, bitrate: 1173 kb/s
    Chapter #0.0: start -0.090233, end 588.611500
    Metadata:
      title           : Chapter  1
    Chapter #0.1: start 588.611500, end 1188.711000
    Metadata:
      title           : Chapter  2
    Chapter #0.2: start 1188.711000, end 1788.310000
    Metadata:
      title           : Chapter  3
    Chapter #0.3: start 1788.310000, end 2388.409500
    Metadata:
      title           : Chapter  4
    Chapter #0.4: start 2388.409500, end 2988.509000
    Metadata:
      title           : Chapter  5
    Chapter #0.5: start 2988.509000, end 3176.697000
    Metadata:
      title           : Chapter  6
    Chapter #0.6: start 3176.697000, end 3182.636267
    Metadata:
      title           : Chapter  7
    Stream #0:0(und): Video: h264 (Main) (avc1 / 0x31637661), yuv420p(tv, smpte170m), 720x480 [SAR 32:27 DAR 16:9], 1008 kb/s, -0.02 fps, 29.97 tbr, 90k tbn, 180k tbc (default)
    Metadata:
      creation_time   : 2012-02-21 02:30:55
    Stream #0:1(eng): Audio: aac (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 159 kb/s (default)
    Metadata:
      creation_time   : 2012-02-21 02:30:55
    Stream #0:2(eng): Subtitle: mov_text (tx3g / 0x67337874), 853x60, 0 kb/s (default)
    Metadata:
      creation_time   : 2012-02-21 02:30:55
    Stream #0:3(und): Subtitle: mov_text (text / 0x74786574)
    Metadata:
      creation_time   : 2012-02-21 02:30:55
[matroska @ 0x3255d00] Subtitle codec 94213 is not supported.
Output #0, matroska, to 'output.mkv':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    encoder         : Lavf55.32.101
    Chapter #0.0: start 0.000000, end 331.611500
    Metadata:
      title           : Chapter  1
    Chapter #0.1: start 331.611500, end 931.711000
    Metadata:
      title           : Chapter  2
    Chapter #0.2: start 931.711000, end 1531.310000
    Metadata:
      title           : Chapter  3
    Chapter #0.3: start 1531.310000, end 2131.409500
    Metadata:
      title           : Chapter  4
    Chapter #0.4: start 2131.409500, end 2731.509000
    Metadata:
      title           : Chapter  5
    Chapter #0.5: start 2731.509000, end 2919.697000
    Metadata:
      title           : Chapter  6
    Chapter #0.6: start 2919.697000, end 2925.636267
    Metadata:
      title           : Chapter  7
    Stream #0:0(und): Video: h264 (avc1 / 0x31637661), yuv420p, 720x480 [SAR 32:27 DAR 16:9], q=2-31, 1008 kb/s, -0.02 fps, 1k tbn, 90k tbc (default)
    Metadata:
      creation_time   : 2012-02-21 02:30:55
    Stream #0:1(eng): Audio: aac ([255][0][0][0] / 0x00FF), 48000 Hz, stereo, 159 kb/s (default)
    Metadata:
      creation_time   : 2012-02-21 02:30:55
    Stream #0:2(eng): Subtitle: mov_text (tx3g / 0x67337874), 853x60, 0 kb/s (default)
    Metadata:
      creation_time   : 2012-02-21 02:30:55
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
  Stream #0:2 -> #0:2 (copy)
Could not write header for output file #0 (incorrect codec parameters ?): Function not implemented



```

---

### Post by FakeOutdoorsman on 2014-02-17
I did not expect subtitles in your input, and I also did not expect Matroska to not like mov_text (AFAIK that is what is occurring). You can add -sn as an output option to ignore the subtitles. Can you provide a small sample of the input?
```
ffmpeg -i input.m4v -t 1 -c copy output.m4v
```

---

### Post by VMC on 2014-02-17
> **FakeOutdoorsman said:**
> I did not expect subtitles in your input, and I also did not expect Matroska to not like mov_text (AFAIK that is what is occurring). You can add -sn as an output option to ignore the subtitles. Can you provide a small sample of the input?
```
ffmpeg -i input.m4v -t 1 -c copy output.m4v
```
Actually I want subtitles.

I used this code to get to the exact time I wanted:
```
ffmpeg -accurate_seek -ss 00:04:21 -i S4e1.mkv -c:v copy -c:a copy output.mkv
```

I know the accurate seek is turned on by default, but used it anyway.

Attach the first 15 seconds of file "out.mkv.tar.bz2". Hope that's enough. If not let me know.

---

### Post by FakeOutdoorsman on 2014-02-17
Your sample works fine for me, but I'm assuming it's a different file than the one you're having issues with since it contains SSA subtitles instead or mov_text and since it is mkv container and not m4v.
```
$ ffmpeg -i out.mkv -ss 2 -t 5 -c copy out2.mkv
ffmpeg version N-60376-g9a4a559 Copyright (c) 2000-2014 the FFmpeg developers
  built on Feb  5 2014 10:59:38 with gcc 4.8.2 (GCC) 20131219 (prerelease)
  configuration: --prefix=/usr --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 63.100 / 52. 63.100
  libavcodec     55. 49.101 / 55. 49.101
  libavformat    55. 30.100 / 55. 30.100
  libavdevice    55.  7.100 / 55.  7.100
  libavfilter     4.  1.102 /  4.  1.102
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 17.104 /  0. 17.104
  libpostproc    52.  3.100 / 52.  3.100
Input #0, matroska,webm, from 'out.mkv':
  Metadata:
    MINOR_VERSION   : 0
    COMPATIBLE_BRANDS: mp42isomavc1
    MAJOR_BRAND     : mp42
    ENCODER         : Lavf55.32.101
  Duration: 00:00:15.07, start: 0.000000, bitrate: 485 kb/s
    Chapter #0.0: start 0.000000, end 15.000000
    Metadata:
      title           : Chapter  1
    Stream #0:0(und): Video: h264 (Main), yuv420p(tv, smpte170m), 720x480 [SAR 32:27 DAR 16:9], SAR 186:157 DAR 279:157, 1k fps, 29.97 tbr, 1k tbn, 180k tbc (default)
    Metadata:
      CREATION_TIME   : 2012-02-21 02:30:55
      LANGUAGE        : und
    Stream #0:1(eng): Audio: aac, 48000 Hz, stereo, fltp (default)
    Metadata:
      CREATION_TIME   : 2012-02-21 02:30:55
      LANGUAGE        : eng
    Stream #0:2(eng): Subtitle: ssa (default)
    Metadata:
      CREATION_TIME   : 2012-02-21 02:30:55
      LANGUAGE        : eng
Output #0, matroska, to 'out2.mkv':
  Metadata:
    MINOR_VERSION   : 0
    COMPATIBLE_BRANDS: mp42isomavc1
    MAJOR_BRAND     : mp42
    encoder         : Lavf55.30.100
    Chapter #0.0: start 0.000000, end 5.000000
    Metadata:
      title           : Chapter  1
    Stream #0:0(und): Video: h264 (H264 / 0x34363248), yuv420p, 720x480 [SAR 186:157 DAR 279:157], q=2-31, 1k fps, 1k tbn, 1k tbc (default)
    Metadata:
      CREATION_TIME   : 2012-02-21 02:30:55
      LANGUAGE        : und
    Stream #0:1(eng): Audio: aac ([255][0][0][0] / 0x00FF), 48000 Hz, stereo (default)
    Metadata:
      CREATION_TIME   : 2012-02-21 02:30:55
      LANGUAGE        : eng
    Stream #0:2(eng): Subtitle: ssa (default)
    Metadata:
      CREATION_TIME   : 2012-02-21 02:30:55
      LANGUAGE        : eng
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
  Stream #0:2 -> #0:2 (copy)
Press [q] to stop, [?] for help
frame=    0 fps=0.0 q=-1.0 Lsize=      98kB time=00:00:05.01 bitrate= 160.7kbits/s    
video:0kB audio:95kB subtitle:0 data:0 global headers:0kB muxing overhead 3.302491%
```

---

### Post by VMC on 2014-02-17
> **FakeOutdoorsman said:**
> Your sample works fine for me, but I'm assuming it's a different file than the one you're having issues with since it contains SSA subtitles instead or mov_text and since it is mkv container and not m4v.

  FakeOutdoorsman, Thanks for all you help. I was confused not really knowing if the file was m4v and not mkv. So I found another in the series, and using handbrake, I made sure it was mkv. Then using this code:
```
ffmpeg -ss 00:03:23 -i S7D3T5.mkv -c:v copy -c:a copy output.mkv
```I was able to cut exactly where I wanted to without issue.

---

### Post by FakeOutdoorsman on 2014-02-18
Good to hear you figured out a solution, but a sample of that troublesome S4e1.m4v might still prove interesting.

---

### Post by VMC on 2014-02-18
> **FakeOutdoorsman said:**
> Good to hear you figured out a solution, but a sample of that troublesome S4e1.m4v might still prove interesting.
I uploaded a sample on post#10. didn't that work?

---

### Post by FakeOutdoorsman on 2014-02-18
That's using the Matroska container format and it contained SSA subtitles, not m4v with mov_text like your input from [post #8](http://ubuntuforums.org/showthread.php?t=2205996&p=12931966&viewfull=1#post12931966).

---

### Post by VMC on 2014-02-18
> **FakeOutdoorsman said:**
> That's using the Matroska container format and it contained SSA subtitles, not m4v with mov_text like your input from [post #8]("http://ubuntuforums.org/showthread.php?t=2205996&p=12931966&viewfull=1#post12931966").
Here is 45 seconds of that S4e1.mv4 file. Her's what I used to get it:
```
$ ffmpeg -i S4e1.m4v -t 45 -codec copy out.m4v
```

[download link]("http://www.tempfiles.net/download/201402/337127/out.html") of first 45 seconds.

---

### Post by VMC on 2014-02-19
I just created another unrelated **mkv** video, and trying to edit out the first 55+ seconds causes the same problem as the original. I'm left with three or four seconds still uncut. 

Using this code:
```
 ffmpeg -ss 00:00:59 -i Minority_Report.mkv -c:v copy -c:a copy out.mkv
```

Maybe from post#6, its not possible to always cut where I want, and I will have to cut further. I wonder what the closest seek point means, or why it can't cut exactly
> ...[COLOR=#202020]*[FONT=Times New Roman]**[I]Note that in most formats it is not possible to seek exactly***, so [/FONT][/I][/COLOR][COLOR=#000000]*ffmpeg *[/COLOR][COLOR=#202020]*[FONT=Times New Roman]will seek to the closest seek point before [/FONT]*[/COLOR][COLOR=#000000]*position*[/COLOR][COLOR=#202020]*[FONT=Times New Roman].[/FONT]*[/COLOR]I'm going to mark this topic as solved based on the above statement, and the fact I only had to do this one time.

---

### Post by varunendra on 2014-02-20
> **VMC said:**
> I wonder what the closest seek point means, or why it can't cut exactly
I know that it happens due to the concept of "**Key Frames**" in lossy codecs.

My belief is (and I'd love to be corrected/enlightened) that **keyframes** are the only frames that contain the 'Full' information (including full image, profile details and exact timestamp) about the frame that is displayed at that very moment. All the other frames in-between contain only Partial information (the rest of the information needed for displaying them is 'Calculated' by different algorithms - hence why these are called "lossy" codecs) that is not sufficient to make them a 'Starting' (or 'Ending') frame of the stream.

If the program splitting such a stream adds the 'Calculated' information to such an intermediate frame to make it 'Complete', it would be tampering with the original stream and may cause profile or compliance issues. At the very least it would not exactly be just a 'splitting', because the original information was changed (if done this way). Hence why the Splitting ALWAYS occurs only at KeyFrames to maintain originality (and probably compatibility too).

Now suppose the keyframes were set to occur every 10 seconds when the source stream was encoded.
Then, if you choose to split the stream at a time that is not a multiple of 10, say for example 122 seconds, then the actual splitting would occur at 130 seconds (a multiple of 10) so that the point that you intended to split at is INCLUDED in the former part (splitting it at 120 would have excluded it).

But that also means that you will be losing an initial 8 second clip in the later part - that's just a price paid for following the rules.

Once again, I'd like to Clarify that the above is _just my assumption_ based on some random information I have come across at different times, and may be totally wrong.

---

### Post by SeijiSensei on 2014-02-20
That's a pretty accurate presentation of how video compression works, Varun.

If you've ever made an [animated GIF]("http://forums.animesuki.com/showthread.php?p=3141700#post3141700"), you might have encountered a similar situation.  Compressed GIFs include a static background frame and various other frames that include only the changes between frames.  Video compression works the same way.  There are "key" frames with a complete image, and differenced frames that display properly only when combined with the preceding key frame.  You cannot cut these videos at any frame other than a key frame.

---

### Post by qyot27 on 2014-02-20
> **varunendra said:**
> I know that it happens due to the concept of "**Key Frames**" in lossy codecs.

My belief is (and I'd love to be corrected/enlightened) that **keyframes** are the only frames that contain the 'Full' information (including full image, profile details and exact timestamp) about the frame that is displayed at that very moment. All the other frames in-between contain only Partial information (the rest of the information needed for displaying them is 'Calculated' by different algorithms - hence why these are called "lossy" codecs) that is not sufficient to make them a 'Starting' (or 'Ending') frame of the stream.
Kinda sorta.

In actuality, there's several different types of frames.  Intra-frames (I frames), Predictive frames (P frames), Bidirectionally-predicted frames (B frames, introduced - or at least popularized - with MPEG-1), IDR frames (I'm really not sure of the exact differences these have from I frames, but they show up with some of the newer formats like H.264), and I think HEVC might add one or two new types also, IIRC.

Usually, keyframes and I frames are one and the same, in that keyframes are set on a group of pictures' starting I frame.  This is because I frames store the entire image.  P frames store a difference to the previous frame, and B frames store the difference between the previous and next frame.  In and of themselves, this doesn't mean the codec is lossy.  You can have lossless codecs with P frames (not sure about B frames, though; it'd be rarer to find for sure), in which case they may actually be referred to as Delta frames - CorePNG is an example of a lossless video codec that utilized delta frames.  The reason this is uncommon to find in lossless codecs is because lossless formats are usually intended for editing in an NLE and for low latency seeking, and the presence of P/B frames don't lend themselves easily to these tasks (not that they *couldn't* be, it'd just make the process more complex than is necessary).  For archival purposes, lossless formats with inter-frame coding would allow for better storage usage.  The reverse also occurs - there are fully intra-frame formats that are lossy, like MJPEG and DV (or really, any other lossy format where the user explicitly forces intra frames only).

What actually causes the lossless/lossy divide is that using various perception-modelling algorithms, you can cut out parts of the signal the human eye can't perceive, and this drastically reduces filesize - how much you cut out (or said another way, how much strength you give to the algorithm) is what causes the visible loss and artifacts to start appearing.  This occurs on both I frames (as anyone that's ever seen regular JPEG files that have been heavily compressed can tell you), and on P and B frames.  The thing about the P and B frames is that you can actually compress them even more than the I frames while still having a decent quality output image, due to the ways that motion compensation and the human eye and such end up working.  A lossless format by definition is mathematically identical to the original on decompression, a lossy format is not and cannot (and that's it; the quality of a lossy codec is determined by how much got cut out of the signal - set a high enough bitrate, and the result will be transparent to the original, meaning it appears to be *visually* identical...but visual identicalness is subjective whereas mathematic identicalness is absolute).

---

### Post by varunendra on 2014-02-21
Aha, Thanks for the confirmation SeijiSensei !

I have created animated GIFs (looong ago, in my Windows days), but probably not the kind you mentioned. The ones I created were just stored as sequences of multiple images with defined timings (at least that's what I think, or how "Irfan View" type programs report about them). So probably compressed GIFs are a different beast. :)

And qyot27, your post is the best explanation of all-those-things-in-one-place that I have come across. All the previous information I have read about these so far (not my field, just read at random times in random contexts) was either too scattered or too detailed for me to absorb.

I had the 'JPEG' images in mind when I was writing about Full vs Incomplete frames w.r.t. Lossy vs Lossless codecs. But my existing knowledge about their underlying principles is dangerous enough to further confuse the topic rather than clarify anything, that's why I didn't focus on it. :P

Thanks for taking time to explain them for us. I just bookmarked your post for future reference and I'm glad I posted what I knew. :)

---


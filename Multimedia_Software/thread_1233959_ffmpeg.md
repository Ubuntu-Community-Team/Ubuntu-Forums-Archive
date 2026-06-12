---
title: "ffmpeg"
date: 2009-08-07
forum: Multimedia Software
---

### Post by Jimstehrman on 2009-08-07
hi, I'm running ffmpeg through terminal on my politely useless mac.
I noticed that when a video is cut (segmented) the resulting video is much worse quality than the original, is there a way to prevent this?

thanks a bunch

---

### Post by FakeOutdoorsman on 2009-08-07
Show your FFmpeg command and the full output.

---

### Post by Jimstehrman on 2009-08-11
found a fix, it just takes a -sameq command at the start.

---

### Post by FakeOutdoorsman on 2009-08-11
You're performing an unnecessary re-encode with *-sameq* (assuming you're not changing formats).  You can copy the audio and video streams and avoid re-encoding with:
```
ffmpeg -ss 1:20 -t 15 -i input.mpg -acodec copy -vcodec copy output.mpg
```
[indent]**-ss**: skip the first 1 minute 20 secods of video
**-t**: copy the next 15 seconds of input.mpg into output.mpg
**-acodec copy**: copy the audio stream
**-vcodec copy**: copy the video stream[/indent]

---

### Post by Jimstehrman on 2009-08-11
this seems to make the process take much longer, and produces files the same size as the original, here is my script


    ffmpeg -sameq -ss $x  -t $dur -i "$in.mov" "$out.mov"
 
and you say:

    ffmpeg -ss $x -t $dur -1 "$in.mov" -acodec copy -vcodec copy "$out.mov"
 
this seems strange to me, can you explain? thanks again though

---

### Post by FakeOutdoorsman on 2009-08-11
> **Jimstehrman said:**
> this seems to make the process take much longer, and produces files the same size as the original, here is my script
Using *-acodec copy* and *-vcodec copy* should always be faster than re-encoding unless there is an error, corrupt input file, or incorrect syntax.

> ```
ffmpeg -sameq -ss $x  -t $dur -i "$in.mov" "$out.mov"
```

Your syntax is incorrect.  Options used before *-i* apply to the input file.  Options used after *-i* apply to the output file. If you want to use *-sameq* then you have to place it after *-i*.  I'm not sure how FFmpeg will interpret the *-sameq* option on the input file.

> and you say:
```
ffmpeg -ss $x -t $dur [color=#FF0000]-1[/color] "$in.mov" -acodec copy -vcodec copy "$out.mov"
```
this seems strange to me, can you explain? thanks again though
You used*-1* instead of *-i* in your example above.  What my example does is ignore the first 1 minute and 20 seconds of the input then copy the following 15 seconds of video and audio from the input into the output.  It is not re-encoding.  It's like copying and pasting text from one file of the same format to another file of the same format.

---

### Post by Jimstehrman on 2009-08-12
this is the feedback I get from your code:
 code:
FFmpeg version SVN-r19605, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-libmp3lame --enable-shared --disable-mmx
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.37. 0 / 52.37. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Aug  7 2009 10:48:47, gcc: 4.0.1 (Apple Inc. build 5465)

Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'example satellite.mov':
  Duration: 00:09:13.29, start: -210.-145145, bitrate: 8180 kb/s
    Stream #0.0(eng): Video: yuvu / 0x75767579, 640x480, PAR 1:1 DAR 4:3, 29.97 tbr, 2997 tbn, 2997 tbc
    Stream #0.1(eng): Data: tmcd / 0x64636D74
    Stream #0.2(eng): Audio: pcm_s16be, 44100 Hz, 2 channels, s16, 1411 kb/s
Output #0, mov, to '1.mov':
    Stream #0.0(eng): Video: yuvu / 0x75767579, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 2997 tbn, 2997 tbc
    Stream #0.1(eng): Audio: pcm_s16be, 44100 Hz, 2 channels, s16, 1411 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.2 -> #0.1
Press [q] to stop encoding
frame=  472 fps= 30 q=-1.0 size=  285910kB time=225.86 bitrate=10370.0kbits/s   frame=  482 fps= 30 q=-1.0 size=  291968kB time=226.19 bitrate=10574.1kbits/s   frame=  499 fps= 30 q=-1.0 size=  302266kB time=226.76 bitrate=10919.7kbits/s   frame=  519 fps= 30 q=-1.0 size=  314381kB time=227.43 bitrate=11324.0kbits/s   frame=  534 fps= 30 q=-1.0 size=  323467kB time=227.93 bitrate=11625.7kbits/s   frame=  554 fps= 30 q=-1.0 size=  335581kB time=228.60 bitrate=12025.9kbits/s   frame=  575 fps= 30 q=-1.0 size=  348317kB time=229.40 bitrate=12438.7kbits/s   frame=  592 fps= 30 q=-1.0 size=  358661kB time=230.23 bitrate=12761.7kbits/s   frame=  610 fps= 30 q=-1.0 size=  369567kB time=230.83 bitrate=13115.5kbits/s   frame=  635 fps= 30 q=-1.0 size=  384708kB time=231.67 bitrate=13603.7kbits/s   frame=  656 fps= 30 q=-1.0 size=  397430kB time=232.37 bitrate=14011.2kbits/s   frame=  671 fps= 30 q=-1.0 size=  406516kB time=232.87 bitrate=14300.7kbits/s   frame=  692 fps= 30 q=-1.0 size=  419238kB time=233.57 bitrate=14704.0kbits/s   frame=  710 fps= 30 q=-1.0 size=  430142kB time=234.17 bitrate=15047.8kbits/s   frame=  727 fps= 30 q=-1.0 size=  440437kB time=234.74 bitrate=15370.6kbits/s   frame=  747 fps= 30 q=-1.0 size=  452555kB time=235.40 bitrate=15748.8kbits/s   frame=  764 fps= 30 q=-1.0 size=  462853kB time=235.97 bitrate=16068.4kbits/s   frame=  782 fps= 30 q=-1.0 size=  473755kB time=236.57 bitrate=16405.2kbits/s   frame=  798 fps= 30 q=-1.0 size=  483445kB time=237.11 bitrate=16703.0kbits/s   frame=  816 fps= 30 q=-1.0 size=  494349kB time=237.71 bitrate=17036.6kbits/s   frame=  836 fps= 31 q=-1.0 size=  506463kB time=238.37 bitrate=17405.2kbits/s   frame=  852 fps= 31 q=-1.0 size=  516158kB time=238.91 bitrate=17698.7kbits/s   frame=  867 fps= 30 q=-1.0 size=  525244kB time=239.41 bitrate=17972.6kbits/s   frame=  886 fps= 31 q=-1.0 size=  536754kB time=240.04 bitrate=18318.0kbits/s   frame=  903 fps= 31 q=-1.0 size=  547048kB time=240.61 bitrate=18625.3kbits/s   frame=  912 fps= 30 q=-1.0 Lsize=  552516kB time=240.91 bitrate=18788.0kbits/s  

the correct amount of files are created, but each file is the exact size of the parent file.

for good measure here is the working part I used:

code:
x=0
in="example satellite" #enter the name of desired file to split
out=1       
dur=5        #enter desired duration of segment (see help file)
endtime=30  #enter total length of desired file (in sec)
while [ "$x" -le "$(($endtime - $dur))" ]
    do
    ffmpeg -ss $x  -t $dur -i "$in.mov" -acodec copy -vcodec copy "$out.mov"
    x=$(($x + $dur))
    out=$(($out + 1))
done

---

### Post by FakeOutdoorsman on 2009-08-12
```
the correct amount of files are created, but each file is the exact size of the parent file.
```
Do you mean that FFmpeg is ignoring your *-ss* and *-t*?  Try using FFmpeg directly.  If it works then your script is the problem.

---


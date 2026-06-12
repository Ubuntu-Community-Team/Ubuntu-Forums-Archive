---
title: "Better option for converting (or just playing) mts format video?"
date: 2008-12-07
forum: Multimedia Software
---

### Post by ddixonr on 2008-12-07
I've been searching for months for a feasible option for converting mts clips from my Canon vixia hf100. I've tried the m2tstoavi script that lots of people refer to, but the video looks terrible when I do it and it doesn't have any sound.

I would really appreciate some good advice on this one. Thanks.

---

### Post by ddixonr on 2008-12-07
Apologetic bump.

---

### Post by benerivo on 2008-12-07
Maybe try ffmpeg or mencoder from the command line. It may also help if you have the medibuntu restricted packages installed. For ffmpeg try```
ffmpeg -i 00011.MTS -f avi -vcodec mpeg4 -b 9600000 -acodec ac3 -ab 512000 -s 854x480 test3.avi
```where -b 9600000 is the video bitrate, -ab 512000 is the audio bitrate, 00011.MTS is the input video and test.avi is the output. The input and output files need to be in your home directory, otherwise the full file path is needed.

---

### Post by FakeOutdoorsman on 2008-12-07
What do you want to convert to?  I've been able to re-encode from h264 mts (Panasonic HMC-150) to resized h264 using ffmpeg with the libx264 presets.  Unfortunately, you will have to compile ffmpeg and x264 yourself to take advantage of these because Ubuntu's ffmpeg is too old:

[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

If you don't want to compile ffmpeg you should at least try ffmpeg from the repo with a simple:
```
ffmpeg -i input.mts output.mpg
```

> **benerivo said:**
> 
...
It may also help if you have the medibuntu restricted packages installed.
There is no Medibuntu ffmpeg for Intrepid.  You have to either compile it yourself or install the [unstripped ffmpeg libraries]("http://ubuntuforums.org/showpost.php?p=6197965&postcount=11") [link to forum post].

---

### Post by benerivo on 2008-12-07
Yes sorry, medibuntu doesn't include any ffmpeg additions. I did try the basic ffmpeg command line (as FakeOutdoorsman provides) on a sample .MTS file (just past half way down [this link]("http://www.camcorderinfo.com/bbs/showthread.php?t=132542&page=1")), but it failed. The command line i gave above, created a useable file, but the audio stopped towards the end, and i'm not sure it was playing at the correct frame rate. There's plenty of ffmpeg video conversion guides on the web that might help.

---

### Post by ddixonr on 2008-12-10
```
Press [q] to stop encoding
[h264 @ 0xb7e339a8]PAFF interlacing is not implemented
[h264 @ 0xb7e339a8]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0xb7e339a8]PAFF interlacing is not implemented
[h264 @ 0xb7e339a8]illegal short term buffer state detected
[h264 @ 0xb7e339a8]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0xb7e339a8]PAFF interlacing is not implemented
[h264 @ 0xb7e339a8]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0xb7e339a8]PAFF interlacing is not implemented
[h264 @ 0xb7e339a8]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0xb7e339a8]PAFF interlacing is not implemented
[h264 @ 0xb7e339a8]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0xb7e339a8]PAFF interlacing is not implemented3.0kbits/s    
[h264 @ 0xb7e339a8]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0xb7e339a8]PAFF interlacing is not implemented
[h264 @ 0xb7e339a8]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0xb7e339a8]PAFF interlacing is not implemented
[h264 @ 0xb7e339a8]illegal short term buffer state detected
[h264 @ 0xb7e339a8]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0xb7e339a8]PAFF interlacing is not implemented3.0kbits/s    
[h264 @ 0xb7e339a8]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0xb7e339a8]PAFF interlacing is not implemented
[h264 @ 0xb7e339a8]concealing 4080 DC, 4080 AC, 4080 MV errors
Segmentation fault

```

This is what I get from that command. Oh my god. I talked my wife into buying this $800 cam for the kids and the only thing I can do with this is to play them on the tv using the camera itself. I'm going NUTS!

---


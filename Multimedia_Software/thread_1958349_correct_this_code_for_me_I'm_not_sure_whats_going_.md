---
title: "correct this code for me? I'm not sure whats going wrong.. MENCODER"
date: 2012-04-14
forum: Multimedia Software
---

### Post by AlexOnVinyl on 2012-04-14
```
alex@griever:~/Videos$ mencoder Immortals.2011.720p.BRRip.x264-x0r.mkv -ovc xvid -xvidencopts bitrate:800 -oac copy -o Immortals-2011-720-.avi
```

and here's the output:

> MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
Error parsing option on the command line: -xvidencopts


I also tried this: 

```
alex@griever:~/Videos$ mencoder Immortals.2011.720p.BRRip.x264-x0r.mkv -ovc xvid bitrate:800 -oac copy -o Immortals-2011-720-.avi
```

and got the following: 
> MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
success: format: 0  data: 0x0 - 0x7a1b4576
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[matroska,webm @ 0xb6b91d80]max_analyze_duration reached
[matroska,webm @ 0xb6b91d80]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (ac3), -aid 0, -alang eng
[lavf] stream 2: subtitle (text), -sid 0, -slang eng
VIDEO:  [H264]  1280x690  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x34363248  size:1280x690  fps:23.976  ftime:=0.0417
xvid: using library version 1.3.2 (build xvid-1.3.2)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
audiocodec: framecopy (format=2000 chans=6 rate=48000 bits=0 B/s=56000 sample-0)
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Pos:   0.0s      2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.004 [0:0]
Movie-Aspect is 1.86:1 - prescaling to correct movie aspect.
videocodec: XviD (1280x690 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=1280x690, sampled=1280x690
xvid: you must specify one or a valid combination of 'bitrate', 'pass', 'fixed_quant' settings
FATAL: Cannot initialize video driver.

Please help correct my code?

---

### Post by enkay009 on 2012-04-14
It's been a while since I've used mencoder so I may not have the definitive answer for you. I used to downscale video all the time for my old portable device. So I dug around in my old scripts and this is what I found.

Encoding options are seperated by semicolon ( : )

So when you wrote...
```
-xvidopts bitrate:800
```

... mencoder thought you were specifying two different options. One called bitrate and one called 800. It didn't understand that you meant the value.

Try this instead...
```
-xvidencopts bitrate=800
```

And if you have another option (like two pass encoding), you'd modify that to...
```
-xvidencopts bitrate=800:pass=2
```

---

### Post by AlexOnVinyl on 2012-04-16
> **enkay009 said:**
> It's been a while since I've used mencoder so I may not have the definitive answer for you. I used to downscale video all the time for my old portable device. So I dug around in my old scripts and this is what I found.

Encoding options are seperated by semicolon ( : )

So when you wrote...
```
-xvidopts bitrate:800
```

... mencoder thought you were specifying two different options. One called bitrate and one called 800. It didn't understand that you meant the value.

Try this instead...
```
-xvidencopts bitrate=800
```

And if you have another option (like two pass encoding), you'd modify that to...
```
-xvidencopts bitrate=800:pass=2
```

How can I set it to do both a 1 and 2 pass in 1 process?

---

### Post by AlexOnVinyl on 2012-04-16
Bump

---

### Post by enkay009 on 2012-04-16
> **AlexOnVinyl said:**
> How can I set it to do both a 1 and 2 pass in 1 process?

They're mutually exclusive options.

pass=1 means single pass
pass=2 means double pass (not pass #2)

---

### Post by AlexOnVinyl on 2012-04-16
Would you be able to help me out with making this into a bash script?

I need to some how fit the `$f` into the script so that I can right click and execute the script and it fills in the filename with the one selected?

---

### Post by enkay009 on 2012-04-16
> **AlexOnVinyl said:**
> Would you be able to help me out with making this into a bash script?

I need to some how fit the `$f` into the script so that I can right click and execute the script and it fills in the filename with the one selected?

I don't mean to palm you off to the Internet, but... have a look at this guide:

[http://linuxconfig.org/Bash_scripting_Tutorial](http://linuxconfig.org/Bash_scripting_Tutorial)

It's gives you some examples that you can play with to get a feel for Bash scripting (passing arguments, if/else, loops, etc.). If you're like me and you learn by doing, I suggest you try the examples and make slight modifications to understand exactly what it's doing.

And then if you want to further your Bash education: 

[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

I remember going through one of those when I started using Linux seriously. The last one I still use as a reference today.

---

### Post by AlexOnVinyl on 2012-04-16
> **enkay009 said:**
> I don't mean to pawn you off to the Internet, but... have a look at this guide:

[http://linuxconfig.org/Bash_scripting_Tutorial](http://linuxconfig.org/Bash_scripting_Tutorial)

It's gives you some examples that you can play with to get a feel for Bash scripting (passing arguments, if/else, loops, etc.). If you're like me and you learn by doing, I suggest you try the examples and make slight modifications to understand exactly what it's doing.

And then if you want to further your Bash education: 

[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

I remember going through one of those when I started using Linux seriously. The last one I still use as a reference today.

no worries man, yeah ive been using Ubuntu since August of last year and it was at first hectic but now a lot of things are very useful, better than just point and click like how Windows was haha

---

### Post by AlexOnVinyl on 2012-04-17
> **enkay009 said:**
> I don't mean to palm you off to the Internet, but... have a look at this guide:

[http://linuxconfig.org/Bash_scripting_Tutorial](http://linuxconfig.org/Bash_scripting_Tutorial)

It's gives you some examples that you can play with to get a feel for Bash scripting (passing arguments, if/else, loops, etc.). If you're like me and you learn by doing, I suggest you try the examples and make slight modifications to understand exactly what it's doing.

And then if you want to further your Bash education: 

[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

I remember going through one of those when I started using Linux seriously. The last one I still use as a reference today.

I keep getting the following when trying to encode the audio > file: MP3 audio selected.
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81


Here's the command I'm running:
 alex@griever:~```
/Videos$ mencoder Immortals.2011.720p.BRRip.x264-x0r.mkv -ovc xvid -xvidencopts bitrate=800:pass=2 -oac mp3lame -lameopts vbr=1 -o Immortals.2011.720p.BRRip.xviD.avi
```

---------------------------------

Some more output:
> 1 duplicate frame(s)!
Pos:   1.2s     29f ( 0%)  0.00fps Trem:   9min  47mb  A-V:0.084 [98:169]]

Skipping frame!
Pos:   1.9s     48f ( 0%) 13.11fps Trem:  56min 285mb  A-V:0.051 [1081:192Pos:   2.0s     49f ( 0%) 12.24fps Trem:  61min 310mb  A-V:0.055 [1170:193Pos:   2.0s     50f ( 0%) 12.10fps Trem:  63min 323mb  A-V:0.051 [1201:195


---


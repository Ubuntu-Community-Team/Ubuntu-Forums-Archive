---
title: "Remove Logo / Watermark"
date: 2012-09-20
forum: Multimedia Software
---

### Post by alfirdaous on 2012-09-20
Hello everybody,

Is there a way to remove logo / watermark from a video using FFMPEG solution or any other program in a command line.

Thank you in advance

---

### Post by BicyclerBoy on 2012-09-20
There are videofilters in ffmpeg & mplayer (delogo)

grossly simplied cmd line:
ffmpeg -i inputfile -vf "delogo" out.mpg

Can set the active "delogo" region of the video frame.
[http://ffmpeg.org/ffmpeg.html#delogo](http://ffmpeg.org/ffmpeg.html#delogo)

Might have to build your ffmpeg or use Jon Severrisson ppa to get video-filters.
Think the mplayer delogo feature has been around for sometime..

---

### Post by QIII on 2012-09-20
Does the logo/watermark indicate copyright information, etc?

---

### Post by alfirdaous on 2012-09-20
@BicyclerBoy: Oh, thanks

```

ffmpeg -i 4wX5bMF_a_s.mp4 -vf "delogo=x=10:y=100" out.mp4

[delogo @ 0x806ae20] Option w was not set.
Error initializing filter 'delogo' with args 'x=10:y=100'
Error opening filters!

```

@QIII: it is a website written there

---

### Post by BicyclerBoy on 2012-09-20
Post the ffmpeg version..

Like I said before ? you need a recent ffmpeg build..
ffmpeg has been replaced (in Ubuntu) by libav project "avconv"

Your cmd is complaining that w is not set..so set w...

I'm using this
ffmpeg version 0.10.4-6:0.10.4-0ubuntu0jon2
& this cmd is valid syntax:
ffmpeg -f v4l2 -i /dev/video0 -vf "delogo=x=0:y=0:w=100:h=77:band=10" out.mpg

---

### Post by alfirdaous on 2012-09-20
```

Version: 6:0.10.4-0ubuntu0jon2~lucid2

```

this is the output result:

```

[video4linux2,v4l2 @ 0x806f020] ioctl(VIDIOC_QUERYCAP): Inappropriate ioctl for device
4wX5bMF_a_s.mp4: Inappropriate ioctl for device

```

---

### Post by BicyclerBoy on 2012-09-20
My cmd line was just **syntactically correct** not a useful cmd for you..

My cmd captures my netbook webcam & delogos it..just rework your command..

Your cmd is complaining that w is not set..so set w...

---

### Post by alfirdaous on 2012-09-20
something like:

```

$ ffmpeg -i trimmed.mp4 -strict experimental -vf "delogo=x=20:y=350:w=100:h=100:band=100:show=1" outTrimmed.mp4

```

Can we make any background color?

---

### Post by BicyclerBoy on 2012-09-20
The :show=1 colour could be fixed..maybe the band value can change it..
The green colour block is to help you set the x:y:w:h values..

:show=0 (the default value) replaces logo with pixels interpolated from surroundings..  
:band might work better with values like 2 to 20 & not =100..

---

### Post by alfirdaous on 2012-09-20
Thx[BicyclerBoy]("http://ubuntuforums.org/member.php?u=816321")

I'll play around these options and get back to you
[]("http://ubuntuforums.org/member.php?u=816321")

---


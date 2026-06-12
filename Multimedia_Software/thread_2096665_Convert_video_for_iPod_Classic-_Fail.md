---
title: "Convert video for iPod Classic- Fail"
date: 2012-12-20
forum: Multimedia Software
---

### Post by PDA1 on 2012-12-20
I've asked this question too many times.  Also, I know what works and doesn't work on my system which is Ubuntu 12.04 (the other machine is 10.04).

I'm not too successful lately in converting videos to be played on my iPod 160G Classic.

Trust me- it's really frustrating to say the least!

The problem occurs with videos over 16 minutes or so and at around the 16 minute mark they speed up for a few seconds and run all the way to the end of
the video and stop.

Yes, I can download any mp4 video that's 10 minutes or less and install it on my iPod using Gtk-Pod .9.9 something-or-another using Ubuntu 10.04

Before you read the ffmpeg code I use here's what doesn't work on my machine for converting videos to iPod Classic compatible format;

- Avidemux

- Handbrake

- MP4ize (never could figure out how to install or use "the simple script" that you can find around the web.

-kdenlive

- mencoder

- womencoder (that's just a joke folks)

- VLC


Here's the ffmpeg code I'm using;

ffmpeg -i I**nput_File_Name.mp4** -vcodec libx264 -preset ultrafast -vpre ipod320 -crf 24 -acodec libfaac -aq 100  -vf scale="320:trunc(ow/a/2)*2"  **Output_File_Name.mp4**

iPod Classic (160G) is not iPod Touch.

Certainly there has to be a way to fix this problem. I can't be the only one struggling to solve this. I've looked all over the web and tried all of those "easy to convert to iPod" programs/ffmpeg- codes and none of them will solve this particular situation.

Do you have any idea what's going wrong?

Do you have first hand experience in solving this problem?

Thank you.

---

### Post by dannyboy79 on 2012-12-20
almost everyone one of those gui's you listed uses ffmpeg to do it transcoding. does it happen on ALL your 16+ minute videos or only 1 video?

---

### Post by PDA1 on 2012-12-20
It only happens on the videos I've downloaded lately.

Several months ago I added many home  videos, converted them using the aforementioned code and they play perfectly on my iPod.

The recent downloads suffer the problem I mentioned.

---

### Post by andrew.46 on 2012-12-23
Are you using a recent version of FFmpeg and x264?

---

### Post by evilsoup on 2012-12-23
You could try adding '-profile baseline' (without the quote) to that ffmpeg command, before the output.

---

### Post by FakeOutdoorsman on 2012-12-23
> **PDA1 said:**
> 
```
ffmpeg -i Input_File_Name.mp4 -vcodec libx264 -preset ultrafast -vpre ipod320 -crf 24 -acodec libfaac -aq 100  -vf scale="320:trunc(ow/a/2)*2"  Output_File_Name.mp4
```

Please show the complete ffmpeg console output. I recall having to use "-vpre libx264-ipod320", but I may be experiencing early onset dementia.

> **evilsoup said:**
> You could try adding '-profile baseline' (without the quote) to that ffmpeg command, before the output.

This will duplicate the ipod320 preset if, for some reason, the preset is not working as expected (as to be seen, possibly, with the console output):

```
-profile:v baseline -level 13 -maxrate 768000 -bufsize 3000000
```

This preset is designed for really old iDevices, so I guess it should work for most, if not all, of them.

---


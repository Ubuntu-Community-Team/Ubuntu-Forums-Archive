---
title: "EasyCap DC-60+ em28xx Drivers"
date: 2011-06-29
forum: Multimedia Software
---

### Post by 12apennachi on 2011-06-29
I have been trying for a few days to get my easycap dc60+ to capture on Ubuntu 11.04 and 10.04, with most success on 10.04. From now on I will describe my actions on my 10.04 box:

lsusb reads that is is the em2861, I read about this and saw from multiple sources that the kernel drivers support this. Unfortunately this was not true for me. the device was not found after plugging it in (according to cheese) so i did what anyone would do and got the latest drivers and compiled them from source. Now when I plug it in and try to capture from my vhs into a program, melt, cheese, and kdenlive all show the same thing; a green slimy bar on the bottom of the screen and that is all. On windows it works but the program is so awful it crashes every five minutes and does not record audio. I would really appreciate any help you may have to offer.

---

### Post by philstovell on 2011-06-30
I have an em2860 device (KWorld USB2800D). I also compiled the latest drivers (Ubuntu 10.04).

I use mencoder to capture my ancient VHS videos, I couldn't get cheese etc to work.

This is the command line I use:

```
mencoder tv:// -tv driver=v4l2:norm=PAL:input=1:amode=0:width=720:height=576:device=/dev/video0:alsa:forceaudio:amode=0:audiorate=48000:adevice=hw.0,2 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=6000 -oac mp3lame -lameopts cbr:br=64:mode=3 -mc 0 -noskip -vf pp=ci,harddup -o video.avi
```

I then edit the videos with avidemux.

Here's a short example of a VHS video from 1987 converted using the above method:
[http://www.youtube.com/watch?v=dYRedgQumJI]("http://www.youtube.com/watch?v=dYRedgQumJI")

---

### Post by rmt1947 on 2011-06-30
Hi,

I did manage to get an EasyCAP DC60+ working on Ubuntu 10.10 about six months ago, with some difficulty - see my post #12 in the thread:

[http://ubuntuforums.org/showthread.php?t=1642985](http://ubuntuforums.org/showthread.php?t=1642985)

There might be some information there which would help.  I don't use the DC60+ myself these days, so I'm afraid I won't be able to offer much follow-up advice.

Mike

---

### Post by 12apennachi on 2011-07-01
Thank you guys very much, I will try both (when I get the time, stupid work always cutting in) and will get back to you with the news

---

### Post by ianmillington on 2011-07-08
Here's my experience

I'm at the stage where I can get pretty good video but no audio, and I'm coming to the conclusion that I should by-pass the DC60+ for audio.

I struggled for ages until I realised that the card does not automatically (with Linux anyway) get configured to accept composite input. 

Try loading VLC and select file/open capture device. Ensure you have selected video 4 linux, start your video source and then simply hit play. You will see a blank screen.

Then the magic - load a terminal and type 

v4l2-ctl -d /dev/video0 -i 1

Then hit return. If successful you will see a message that input has been set to composite and you can then close the terminal and should see your video footage. 

The real PITA is the audio, which appears to be a lottery and in 11.04 I suspect has more than a little to do with pulse.

---


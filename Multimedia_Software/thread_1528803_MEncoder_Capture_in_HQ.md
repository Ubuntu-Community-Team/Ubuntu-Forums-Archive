---
title: "MEncoder: Capture in HQ?"
date: 2010-07-11
forum: Multimedia Software
---

### Post by Blue-K on 2010-07-11
First: Hello :). 

Now, I recently bought an EasyCap-Capture Device, and although I know that you can't expect great quality from it, I still try to push it to the limit, and get the best quality as possible. I've found some scripts from an User here, and changed them a bit, though, the videos still [don't look alright on Youtube]("http://www.youtube.com/watch?v=CLp91bicymI") (not full screen/black bars). So I hoped that you could share some tips...

Here's the Script I currently use to record:
```
mencoder -tv driver=v4l2:width=720:height=576:device=/dev/easycap0:forceaudio:alsa:adevice=/dev/easysnd1:immediatemode=0:audiorate=44100:input=1:norm=PAL_60 -noskip -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=6000:aspect=16/9 -oac mp3lame -lameopts mode=1 -o Recorded tv:// 
```After that, I'll deinterlace the video with this script:
```
ffmpeg -i Recorded -target pal-dvd -deinterlace -sameq -aspect 16:9 Final.avi
```I would like to record in the best possible quality (with such a shitty device :P), so no black bars, 16:9, 720p, etc. Thanks in advance!

---


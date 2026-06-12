---
title: "x264 video &amp; AC3 audio sync"
date: 2007-08-01
forum: Multimedia Production
---

### Post by blue42na on 2007-08-01
Howdy folks! I've been using Ubuntu for a few months now and it's great. I apologize for my first post being a question, but I've really been pulling my hair out on this one. 

My question is how can I extract the audio delay info from an AC3 audio file.  

To create the file I'm using the following command: 
```
mplayer test.vob -aid 128 -dumpaudio -dumpfile audio.ac3
```

The video source is a DVD and I'm encoding using x264.  Here are my command lines.
```

mkfifo y4m

mencoder test.vob -msglevel all=-1 -nosound -ovc raw -vf format=i420 -of rawvideo -o y4m

/usr/local/bin/x264 -o office.264 --crf 30 --progress --fps 29.970 --sar 32/27 y4m 720x480

```

Anyways, I'm having horrible sync issues.  I was using MeGUI on windows and it always took care of the delay itself.  This one is really killing me.  

Any help you can provide would be greatly appreciated.  Thanks!

---

### Post by krokodil on 2007-08-05
hey blue,

I'm new to encoding with x264 myself.

Looking at your cmds I'm can't see where you're muxing the streams together, the problem can possibly be fixed during the muxing?

Also I read on the doom9 forums that they are working on a MeGUI port to Linux.

---


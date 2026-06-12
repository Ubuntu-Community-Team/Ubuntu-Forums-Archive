---
title: "mencoder transcoding causes garbled sound"
date: 2007-10-11
forum: Multimedia &amp; Video
---

### Post by coolfrood on 2007-10-11
Hi,

I'm trying to use mencoder to transcode videos.  The video gets transformed OK but the audio is completely garbled.  This happens no matter what kind of audio output I choose -- I've tried faac and mp3lame.  The only way the audio is okay is if I just use the "-oac copy" option.  Also, it does not matter what kind of video I try to transcode.  Here's the command line that I'm using:

mencoder a.avi -o b.avi -srate 44100 -oac mp3lame -lameopts vbr=0;br=96 -ovc lavc -lavcopts vcodec:mpeg4:vbitrate=96 -vf-add crop 586:352 -vf=add scale=240:144 -ofps 12.5 -ffourcc DIVX -noidx -force-avi-aspect 1.6666667


mencoder version 2:1.0~rc1-0ubuntu9
liblame0 version 3.96.1-2ubuntu1

Any ideas? 

Thanks,
Akhat

---

### Post by coolfrood on 2007-10-11
More info: I am able to get proper sound on another machine that is also running feisty.  I looked at the versions of the packages and also the list of libraries that are loaded by mencoder.  All of them look the same, and yet one machine produces garbled sound in the video while the other doesn't.

---


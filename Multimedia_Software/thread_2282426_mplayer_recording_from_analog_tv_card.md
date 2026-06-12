---
title: "mplayer recording from analog tv card"
date: 2015-06-14
forum: Multimedia Software
---

### Post by white123 on 2015-06-14
hello there!

I started using linux because it is great system and my old analog tv card is working today (windows 7 and newer are not supported).

I was using tvtime for watching tv channels but tvtime cannot record so I switched to mplayer.

For wathcing tv, this command works for me:

```
mplayer tv:// -tv driver=v4l2:norm=PAL:input=0:amode=1:width=704:height=480:outfmt=yv12:device=/dev/video0:chanlist=europe-west:channel=SE5
```

and I would like to record TV to file. So far, the command below is writing to file, but I dont know how to stop recording (kill process is not working because the capture file cannot be then played in any player).

```
mplayer tv:// -tv driver=v4l2:norm=PAL:input=0:amode=1:width=704:height=480:outfmt=yv12:device=/dev/video0:chanlist=europe-west:channel=SE5 --dumpvideo --dumpfile=/home/testuser/Desktop/filetest.avi
```

so if anyone can help me to: record my analog tv to file and

maybe to use some encoding, because the recorded file is not very small after some time.

I would like to record for example for 3 hours. and then, automatically turn off the pc.

Thank your for your help!

edit: this code captures, audio is good but video is very fast..

mencoder tv:// -tv  driver=v4l2:width=720:height=576:norm=PAL:outfmt=uyvy:device=/dev/video0:input=0:fps=25:alsa:amode=1:forcechan=2:audiorate=48000:adevice=plughw.1,0:forceaudio:immediatemode=0  -msglevel all=9 -ffourcc DX50 -ovc lavc -lavcopts  vcodec=mpeg4:mbd=2:turbo:vbitrate=1200:keyint=100 -vf  pp=lb,scale=640:480 -oac mp3lame -o test.avi

---

### Post by white123 on 2015-06-14
ok, the problem was solved adding -noskip into the command.

working full command:

```
 mencoder tv:// -tv channel=0:driver=v4l2:device=/dev/video0:normid=4:input=0:chanlist=europe-west:width=704:height=480:audiorate=44100:alsa:adevice=hw.1:brightness=0:contrast=0:hue=0:saturation=0 -oac copy -ovc lavc -noskip -quiet -vf scale=704:480 -lavcopts vcodec=mpeg4:vbitrate=3000 -o ./vidfile.avi
```

---


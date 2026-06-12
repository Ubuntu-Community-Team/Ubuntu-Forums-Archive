---
title: "USB Video Capture in VLC or kdenlive"
date: 2009-09-10
forum: Multimedia Software
---

### Post by LordKaT on 2009-09-10
Hey folks, I'm having some problems with USB video capture.

I'm using a Pinnacle DVD Recorder (DVC100) plugged in via USB, and using Video4Linux2.

video is streamed on /dev/video1
audio is streamed on /dev/dsp1

In kdenlive, I can *play* the audio and video fine, but when I try to capture it, the video is fine (except for a green bar at the bottom), but the audio is screwed up (it sounds like crystals breaking, if that makes any sense).

VLC is unable to play audio (says it is unable to access /dev/dsp1), and it only plays video at a resolution of 144x96 (the real resolution is 720x480). If I try to manually set the resolution, VLC is unable to play the video.

Another interesting problem is that in both kdenlive and VLC there is a large green second at the bottom - something that is not present if I view the video on tvtime.

Any ideas?

---

### Post by LordKaT on 2009-09-11
While I did not manage to figure out just what is wrong with eithr VLC or kdenlive, I did manage to figure out how I can capture video from my Pinnacle Dazzle DVD USB capture device, by using streamer (look for it in synaptic):


streamer -s 720x480 -c /dev/video1 -C /dev/dsp1 -r 30 -f jpeg -F mono16 -t 00:30 -o stream.avi -d


This will record 30 seconds (-r 00:30) of video from the device. I'd prefer something that continually records until interrupted, but this will do for my purposes.

There's still the issue of a large green bar at the bottom of the video, which doesn't appear in windows. This isn't too much of a problem, though, as I can pan & scan the video in kdenlive.

---

### Post by rob-ward on 2009-09-11
You may want to have a look at mencoder, it should do everything that you are doing, is likely to encode using less resourced and to better quality, has more options including the ability to crop the input(removing you green bar)

---

### Post by LordKaT on 2009-09-15
After running into a particularly annoying issue with the streamer application mentioned above where the recorded AVI would "skip" like a broken DVD (recording old frames), I looked into mencoder as was suggested, and managed to build this command:

```
mencoder tv:// -tv driver=v4l2:input=0:norm=ntsc:width=720:height=480:outfmt=yuy2:device=/dev/video1:forceaudio:audiorate=48000:adevice=/dev/dsp1 buffersize=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=5000:keyint=30 -oac mp3lame -lameopts br=128:cbr:mode=3 -ffourcc divx -o record.avi
```

I had the hardest time coming up with the :adevice=/dev/dsp1 parameter, which wasn't listed anywhere in the mencoder documentation, and was barely mentioned in a mailing list post.

I'm now able to capture video from the device without the green bar at the bottom, AND the video is already compressed. Now all I need to do is run it through a de-interlacer and all should be well :) Thanks for the suggestion!

---

### Post by dnguyen1963 on 2009-09-21
> **LordKaT said:**
> After running into a particularly annoying issue with the streamer application mentioned above where the recorded AVI would "skip" like a broken DVD (recording old frames), I looked into mencoder as was suggested, and managed to build this command:

```
mencoder tv:// -tv driver=v4l2:input=0:norm=ntsc:width=720:height=480:outfmt=yuy2:device=/dev/video1:forceaudio:audiorate=48000:adevice=/dev/dsp1 buffersize=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=5000:keyint=30 -oac mp3lame -lameopts br=128:cbr:mode=3 -ffourcc divx -o record.avi
```

I had the hardest time coming up with the :adevice=/dev/dsp1 parameter, which wasn't listed anywhere in the mencoder documentation, and was barely mentioned in a mailing list post.

I'm now able to capture video from the device without the green bar at the bottom, AND the video is already compressed. Now all I need to do is run it through a de-interlacer and all should be well :) Thanks for the suggestion!

Hi LordKaT,

I have a lot of old VHS tapes and Dazzle setup on a Windows XP computer.  Needless to say, my Windows XP computer crapped out on me (my wife used it and had tons of viruses downloaded).  I switched this computer over to Ubuntu and found out that Dazzle could not longer work.  Would the suggested command code above work for converting VHS to DVD?  If yes, could you give me some instructions?  I'm a newbie.

Thanks,

Duy

---

### Post by spegru on 2009-11-20
I've just been using an old analogue TV card that has an s-video and composite inputs. Seems to work with a vhs machine, but make sure you have it set to the correct TV system - PAL in my case

---


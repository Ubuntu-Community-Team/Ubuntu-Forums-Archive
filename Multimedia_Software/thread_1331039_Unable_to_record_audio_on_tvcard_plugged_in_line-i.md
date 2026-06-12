---
title: "Unable to record audio on tvcard plugged in line-in"
date: 2009-11-18
forum: Multimedia Software
---

### Post by Elv13 on 2009-11-18
Hi,

I am tring to use SOX to forward alsa hw.0,1 to /dev/dsp1 so I can use mythTV to record video using my tv-card. The card work just fine and the audio cable is plugged into line-in on my sound card.

I can record tv with sound using:
mencoder -tv driver=v4l2:input=2:width=640:height=480:norm=ntsc:chanlist=us-cable:alsa:adevice=hw.0,0  tv://37 -oac copy -ovc copy -o test.avi

All solutions in forums are outdated and don't work anymore, even if they worked with previous Ubuntu version (last time I tried to use sox was with 7.10). What is the right command line?

*Ubuntu 9.10 fresh install
**Pulseaudio is removed as it cause me nightmares.

EDIT: this does not work
```
sudo sox -s -r 32000 -c 2 -t alsa hw:0,0 -s -r 32000 -c 2 -t ossdsp /dev/dsp1
sox soxio: Can't open output file `/dev/dsp1': Unable to reset OSS driver.  Possibly accessing an invalid file/device

```
/dev/dsp1 does not exist so it may be normal

---

### Post by shane2peru on 2009-11-28
You may have to change your mencoder line like this:
```

alsa:adevice=hw.1,0:amode=1:audiorate=32000: -oac pcm

```

Notice the hw.# is different than 0, also amode=1 and audiorate, you can set that to what you want, and then the -oac pcm.  It has been a very long time so I don't remember exactly where or why I used those options, but it seems to work for me. 

Shane

---


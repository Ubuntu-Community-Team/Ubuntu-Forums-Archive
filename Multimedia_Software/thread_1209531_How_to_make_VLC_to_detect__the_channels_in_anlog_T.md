---
title: "How to make VLC to detect  the channels in anlog TV"
date: 2009-07-10
forum: Multimedia Software
---

### Post by gskumar on 2009-07-10
I have  installed VLC and also Tvtime. Tvtime shows all the channels(anlog TV channels, in India),however VLC shows only star ( only one channel) and does not show any other channel. But if TVtime is activated and change channel, then VLC shows only that channel. How to make VLC to show all channels one after the other as TVtime. **The purpose of installing VLC is to record and play back TV programs**. The PC is connected to a cable TV and with Pinnacle analog110i setup/card. Obuntu detects it  and also SAA7133 device. 
I am new to Ubuntu, I request the community to help me.
I do not se any provision in the panel for recording. How do I record program.

---

### Post by tux21 on 2009-07-20
I am from india too

i use this script

#!/bin/sh
gnome-terminal --execute mencoder -tv driver=v4l2:device=/dev/video1:alsa:adevice=hw.1,0:audiorate=48000 -o "TV_RECORDING.AVI" -oac pcm -ovc lavc tv:// 

its one line. change adevice to hw.0,0 if this won't work.  records the last channel u saw in tvtime

---


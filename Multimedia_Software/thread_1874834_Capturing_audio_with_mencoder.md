---
title: "Capturing audio with mencoder"
date: 2011-11-03
forum: Multimedia Software
---

### Post by Artemus on 2011-11-03
Back in Karmic/Lucid days (I believe) I was able to capture video through an SAA7130 and the sound through an old sound blaster ENS1371 card using

 mencoder tv:// -tv driver=v4l2:device=/dev/video0:buffersize=64:fps=29.97:chanlist=us-broadcast:audiorate=32000:adevice=/dev/dsp:input=2:norm=NTSC -ovc copy -oac copy -o out1.mpg

This fails on Natty/Oneiric, apparently due to the switch to Pulse Audio. Pre-pending with padsp gives the error "Unable to open '/dev/dsp': Connection refused."

Can someone tell a correct way to capture the sound now (if any)?

---


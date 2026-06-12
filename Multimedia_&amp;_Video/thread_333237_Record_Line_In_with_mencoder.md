---
title: "Record Line In with mencoder"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by yanewby on 2007-01-07
I am trying to record from an old BT878 TV capture card using mencoder.  The card requires that a cable to be connected from the TV card to the sound card on my PC.  This can either be put into the "Line In" or "Mic" plug on the sound card.

I have successfully managed to record using the following command and using the "Mic" plug:

mencoder -tv driver=v4l2:buffersize=16:norm=PAL:input=0:volume=40:amode=1:fps=25:quality=60:width=640:height=480:device=/dev/video0:chanlist=europe-west:channel=50 tv:// -o test.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1000:keyint=25 -vf lavcdeint -oac mp3lame -lameopts cbr:br=96:mode=0 -endpos 15 -noskip

I would like to be able to use the "Line In" instead.

I understand that I need to tell mencoder where to get the audio from with something like :adevice=/dev/dsp: or :adevice=hw.0: but I do not understand how or where I obtain these values for my PC.  I have only been using Linux and Ubuntu a few months and this is way out of my comfort zone!

I have tried the following with no success (only video - NO AUDIO is recorded) when "Line In" is used:

mencoder -tv driver=v4l2:buffersize=16:norm=PAL:input=0:volume=40:alsa:adevice=hw.0:amode=1:fps=25:quality=60:width=640:height=480:device=/dev/video0:chanlist=europe-west:channel=50 tv:// -o test.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1000:keyint=25 -vf lavcdeint -oac mp3lame -lameopts cbr:br=96:mode=0 -endpos 15 -noskip

mencoder -tv driver=v4l2:buffersize=16:norm=PAL:input=0:volume=40:adevice=/dev/dsp:amode=1:fps=25:quality=60:width=640:height=480:device=/dev/video0:chanlist=europe-west:channel=50 tv:// -o test.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1000:keyint=25 -vf lavcdeint -oac mp3lame -lameopts cbr:br=96:mode=0 -endpos 15 -noskip

In summary, what command do I need to use to enable mencoder to record audio from my PC's "Line In"?

---

### Post by mirceade on 2007-03-28
Same problem here. Waiting advice from the Ubuntu team... :) From what I see, we really, REALLY need a software able to record tv programs without the fuss of the mythtv and with a gui  capable to fully use mencoder (for non-alien users).

---

### Post by dspdude on 2008-06-08
To record TV using mencoder and Line-In, you need to do the following:

1) Mute the line-in to prevent feedback. (For use with MPlayer, not necessary with mencoder)

2) Configure ALSA to capture from "Line". By default it is set to capture from "Mic". 

3) Tell mencoder to use the audio from the sound card. (The "copy" codecs were chosen for brevity.)

Specifically, here are the commands:

amixer sset Line mute cap

mencoder -tv driver=v4l2:norm=ntsc:chanlist=us-cable:adevice=/dev/dsp:audiorate=44100:immediatemode=0:forceaudio tv://29 -oac copy -ovc copy -o tv.avi

---


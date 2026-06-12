---
title: "TV card sound"
date: 2009-10-21
forum: Multimedia Software
---

### Post by grumman on 2009-10-21
i'm using a dazzle tv mobile (external) tv tuner, the video is no problem. However, ubuntu (running 9.10 beta) says that the device only has audio input. if i record from that audio input, i hear the audio of TV station's audio, so for some reason, ubuntu uses the audio output of my tv card as input. Does anyone have an idea how i can either reverse it or listen to the input audio stream in real time (wouldn't be ideal, but at least i'd hae sound)

thx in advance

---

### Post by VertexPusher on 2009-10-22
You need to configure your TV viewer application to route audio from the TV card to the sound card. For example, MPlayer lets you specify the name of the TV sound input device using the -tv configuration option. Once you have done that, MPlayer will read audio data from that device and send it to the default sound card whenever you watch TV.

---

### Post by grumman on 2009-10-22
i can get video in mplayer using:

mplayer -tv driver=v4l2 -vo xv tv://

however, i can't seem to find any options as to how i can redirect the audio input to the output, could you plase give me som more information?

and if i try to use these options:

mplayer -tv driver=v4l2 alsa -vo xv tv://

it says "can ot open file "alsa" (found the alsa parameter in the man pages)

thx in advance

---

### Post by VertexPusher on 2009-10-22
> **grumman said:**
> mplayer -tv driver=v4l2 alsa -vo xv tv://
Try

mplayer -tv driver=v4l2:alsa -vo xv tv://

Note that you also have to specify adevice=... so that MPlayer knows which device to read audio from.

The -vo xv parameter is redundant. MPlayer will automatically use Xvideo for output if available.

Once you have found a working setting, you can save it in MPlayer's config file.

---

### Post by grumman on 2009-10-25
using:

mplayer -tv driver=v4l2 amode=1:alsa:adevice=hw.0,1:amode=2:audiorate=44100:forceaudio:immediatemode=0 -vo xv tv:// 

still doesn't give me sound, i've tried using "adevice=hw.0" , 1, 2, ...
and with the comma "adevice=hw.0,1", both methods don't seem to work

---

### Post by fenian on 2009-10-25
Download Ivtv-Utils from synaptic.
You can set the audio-input like this...

> v4l2-ctl --set-audio-input=1

You may need to use different numbers.

You can set audio output like this...

> v4l2-ctl --set-audio-output=2

Again different numbers may be needed.

---

### Post by VertexPusher on 2009-10-27
> **grumman said:**
> mplayer -tv driver=v4l2 amode=1:alsa:adevice=hw.0,1:amode=2:audiorate=44100:forceaudio:immediatemode=0 -vo xv tv:// 

still doesn't give me sound
You are again omitting colons between the -tv suboptions. It doesn't work that way. You have to stick to the syntax outlined in the manual:

-tv suboption1=value1:suboption2=value2:...

---


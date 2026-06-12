---
title: "Can't capture desktop sound"
date: 2010-10-18
forum: Multimedia Software
---

### Post by oopsie on 2010-10-18
I'm trying to capture my desktop sound ( Video too, but that part's working ) but nothing I try works. I've tried various programmes, none of them work.

I tried various things I read on different websites, and nothing worked. I noticed /dev/dsp was missing, and put it back by a guide, but that made no difference and disappeared again now I rebooted anyway.

So, does anybody have any suggestions about what's going on, and what I can do?

Any help would be appreciated.

---

### Post by oopsie on 2010-10-19
Hate to bump my own posts, but I'm still without a solution. =X

I try to record desktop sound, but no program will do it. None!

/dev/dsp is missing, but maybe it's supposed to be, I don't know, I'm not good at linux =(

Does anybody have any suggestions? I've googled this many times, but not found any results that were helpful yet.

---

### Post by Dan9996 on 2010-10-19
What exactly are you trying to record? Mouse sounds,video sounds, stereo mix (What's coming over the speakers)

---

### Post by chaanakya_chiraag on 2010-10-19
If you want to record what's coming through the speakers, you need to check the inputs to the recording programs to make sure it's not trying to record the stuff coming in through a (nonexistent) mic.

---

### Post by chaanakya_chiraag on 2010-10-19
If you are using PulseAudio (which you are if you are using anything newer than Ubuntu 8.04, when it was introduced into Ubuntu), you should try the following:
1) Install pavucontrol: ```
sudo aptitude -y install pavucontrol
```
2) Start your recording application (GNOME sound recorder, Audacity, etc.)
3) Start PulseAudio Volume Control (It's located in Applications->Sound I think)
4) Start playing the stuff you want to record
5) Go to the PulseAudio Volume Control and move the output stream to the recorder's input stream
6) Start recording!

I'm not sure if this is exactly what you do as I am not on my Linux box at the moment, but I will post back when I have a chance to try it out myself.

---

### Post by oopsie on 2010-10-19
> What exactly are you trying to record? Mouse sounds,video sounds, stereo mix (What's coming over the speakers) 
I'm trying to record the sound my software makes. So yes, what's coming from my speakers.


> If you want to record what's coming through the speakers, you need to check the inputs to the recording programs to make sure it's not trying to record the stuff coming in through a (nonexistent) mic. 
That's probably the problem. I can't seem to find an input that records the sounds of my computer.


> 
If you are using PulseAudio (which you are if you are using anything newer than Ubuntu 8.04, when it was introduced into Ubuntu), you should try the following:
1) Install pavucontrol: 
Already got it installed, and the only thing that seems to reflect the sound my computer makes is "Monitor of Internal Audio Analogue Stereo"


And now for some reason when I record with ffmpeg, it DOES record sound now, when it didn't yesterday. But xVidCap stil doesn't.

Linux confuses the hell out of me some days =\
Well, I'd prefer to use xVidCap since it's easier, but since ffmpeg decides it wants to work today, I'll use it instead.

Thank you chaanakya_chiraag and Dan9996 for replying!

---


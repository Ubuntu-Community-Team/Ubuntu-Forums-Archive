---
title: "no screencapture programs work"
date: 2018-08-01
forum: Multimedia Software
---

### Post by platatomi on 2018-08-01
I have tried every program I can find: recordmydesktop, simplescreenrecorder, kazam, istanbul desktop recorder, and more that I can't remember. None of these programs record any sound, despite me trying every imaginable setting. Some immediately crash, some never save an output file, and some just record a black frame.

The most promising seems to be simplescreenrecorder, because at least it all works besides having no sound. What do I need to do to get one of these programs fully working?


Part of this may be complicated by me having both analog and digital audio outputs, because I have an HDMI video card that I do not use the sound from. I have no idea how to configure the audio recording to work with this particular setup. There don't seem to be any obvious options related to this in simplscreenrecorder.


With simplescreenrecorder, when I choose JACK, it errors out:  "could not connect to JACK"
When I choose ALSA, it errors out: "can't open PCM device"
When I choose PulseAudio, either the monitor or non-monitor records no sound.


Also, Settings show no sound input devices at all. Is this part of the problem and how can I fix it?


Why is this so hard to get working? I have a fully updated 16.04 installation.

---

### Post by TheFu on 2018-08-01
SSR worked 3 days this week on my 16.04.5 laptop.
I do remember having issues picking the correct audio source and I don't use Jack.

For people using Wayland, screen recorders have been an issue (i.e. not working).

---

### Post by platatomi on 2018-08-01
You mean that it worked only three days, and not the other days?

Was it ALSA or Pulseaudio that ended up working somewhat for you?

Is part of the problem the fact that no sound input devices are found? I have been trying fixes for this in particular and nothing has made a difference.

---

### Post by TheFu on 2018-08-01
> **platatomi said:**
> You mean that it worked only three days, and not the other days?

I got it working a few years ago.  Since then, it has always worked for my needs. Most recently, some sports were being streamed live (and wouldn't be available any other way), so I recorded the stream using ssr. It worked perfectly.

> **platatomi said:**
> 
Was it ALSA or Pulseaudio that ended up working somewhat for you?

On my system, Pulse is the controller for ALSA. Different versions of Ubuntu desktops do things differently. I wouldn't assume mine is standard, since I don't run any DE. Inside SSR, the audio backend is listed as "PulseAudio" with source "Monitor of built-in Audio Analog Stereo".   I had to fiddle with pavucontrol to get that part working years ago.  Pulse was crashing on my system every time audio sources/output was changed until to set a config file to prevent shrmem use by Pulse. The Pulse crashing had nothing to do with SSR - it was a Pulse issue and easily reproducable using a browser and any other sound playing program.

> **platatomi said:**
> 
Is part of the problem the fact that no sound input devices are found? I have been trying fixes for this in particular and nothing has made a difference.

You can't record audio if there aren't any devices capable of being recorded.  Might I suggest you work through the "Sound Troubleshooter" first?  Google should find it.
You'll need to know and post much more about your sound hardware to get help.  There is an audio-info script referenced in the multimedia subforum here.  Maybe 5 yrs ago my audio wasn't working. I ran that script and posted the URL in this forum - someone looked at it and was able to tell me exactly what to setup to make audio work. That was a few laptops ago.

---

### Post by Autodave on 2018-08-02
Are you sure that your sound card is capable of playing and recording at the same time?  Some cheaper ones are not capable of doing this.

---

### Post by NM5TF on 2018-08-08
does you SSR screen look similar to mine ???  image here:

[https://imgur.com/a/CbHx8bP](https://imgur.com/a/CbHx8bP)

---

### Post by TheFu on 2018-08-08
My fps is 30, not 120. I only have a Core i3, to 120fps is crazy. 1080i is 30fps. 1080p is 60fps.

---

### Post by NM5TF on 2018-08-08
> **TheFu said:**
> My fps is 30, not 120. I only have a Core i3, to 120fps is crazy. 1080i is 30fps. 1080p is 60fps.

this is how it came up...I did not change anything....works just fine as is...

tommy

---

### Post by kurt18947 on 2018-08-10
I know screen recorders don't use an external microphone but on my machine the default input volume is zero. Would that have a bearing on recording audio? Simple to check.

---

### Post by TheFu on 2018-08-10
> **kurt18947 said:**
> I know screen recorders don't use an external microphone but on my machine the default input volume is zero. Would that have a bearing on recording audio? Simple to check.

SSR let's you choose the audio input.  I've used the internal card, laptop mic, and USB external mics, as setup by Pulse. They all work.

---


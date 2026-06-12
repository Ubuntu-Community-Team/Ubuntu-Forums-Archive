---
title: "Separate input and output devices in ALSA?"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by argotnaut on 2007-07-18
I'm using a Logitech QuickCam Communicate STX with a built-in USB microphone. ALSA sees my integrated soundcard as the default for both input and output. I can select the USB mic in Gnome's mixer and change its volume/muting, but still cannot use this mic with most programs (except Ekiga). For example, the Flash plugin used for video conferencing/email such as Eyejot.com only shows "Linux Microphone" as my only input choice, so it must be using whatever ALSA's default is.

I've found lots of pages about all kinds of complicated things you can do with ALSA using ~/.asoundrc, but I can't find a simple answer to how to do this: how can I tell ALSA that I want my default _output_ card to be hw0,0 but my default _input_ to be hw1,0? Please tell me it can be done ... :)

---

### Post by argotnaut on 2007-07-18
Maybe this will work. According to the [Audacity wiki]("http://audacityteam.org/wiki/index.php?title=USB_mic_on_Linux"), adding the following to ~/.asoundrc works for some users:

```
pcm.!default {
         type asym
         playback.pcm {
                 type plug
                 slave.pcm "hw:0,0"
         }
         capture.pcm {
                 type plug
                 slave.pcm "hw:1,0"
         } 
 }

```

I'll try this and report back.

---

### Post by argotnaut on 2007-07-18
Hmmm, strange results. I tried this, and this _did_ enable the USB microphone in the Flash plugin. However, I could not get any Flash playback. Other playback apps such as Rhythmbox did work.

I also have a Pardus Linux partition on the same machine. With the default Pardus settings, playback works in both Flash and desktop apps. However, the mic works _only_ with Flash.

Anyone have ideas for what to do from here to get everything working all at once?

---


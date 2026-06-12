---
title: "Problem with Audacity"
date: 2016-02-09
forum: Multimedia Software
---

### Post by jacatone on 2016-02-09
Been using Ubuntu 14.04 LTS.  I installed Audacity with the idea of recording streaming internet music. It does work, but the volume on the recording is really low to the point I can barely hear it. Anyone know what I'm doing wrong hear? Thanks.

---

### Post by Dennis N on 2016-02-09
The adjustments on Audacity toolbar for Input Volume and Output Volume don't work (at least in 14.04). You need Pulse Audio Volume Control (recording tab) to adjust the recording levels. You can monitor the source before starting to record, and adjust level using the level indicator on Audacity's toolbar as a guide.

---

### Post by jacatone on 2016-02-09
I don't know which one is the "recording tab". Can't seem to find a user manual for this app. Wish there was just a simple to use streamer recording program I could use instead.

---

### Post by Bucky Ball on 2016-02-09
Pulseaudio you mean? Look at the tab names. Get your stream going, open PAVControl, click 'Input'. Check 'Playback'. You should see the stream in there (scroll down the page if not). Set the port above the stream to the correct device and adjust the slider. That's it.

I've never done what you're doing, but perhaps you need the input tab to be set to whatever you're streaming from and the output tab set to Audacity. Play around and you'll find out. 

Always experiment. Have a poke around in Pulse. Little chance of breaking anything by changing a few ports and sliding a few sliders. 

* Be aware: High noise levels can permanently damage hearing. If you have the volume up high and change the port from the wrong device to the right one and suddenly get sound you will get a blast. Keep levels low when experimenting and slide them up to test. :)

---

### Post by tea for one on 2016-02-10
> **jacatone said:**
> I don't know which one is the "recording tab". Can't seem to find a user manual for this app. Wish there was just a simple to use streamer recording program I could use instead.

I found this tutorial helpful to record with Audacity

[http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html](http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html)

Kind regards

---

### Post by Dennis N on 2016-02-10
> **jacatone said:**
> I don't know which one is the "recording tab". Can't seem to find a user manual for this app. Wish there was just a simple to use streamer recording program I could use instead.

When Audacity starts, you should have the Welcome Window popup. On there are links to the online help and forums. It is well worth your time to look over the documentation for Audacity. Or use Help > Manual > view content online. There are several tutorials on that page.

What is sometimes missed by beginners is that the capture source on the recording tab of Pulse Audio volume control should be set to "Monitor of built-in Audio Analog Stereo" in order to capture streaming audio. Also you can't adjust settings in that tab unless something is actually being recorded or at least monitored.

A simpler recording tool is Audio Recorder. What it lacks (among other things) is the editing capability and the range of file types you can export.

[https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)

But, once Audacity is set up, it remembers it's settings and is ready to go the next time you want to record streaming audio.

---


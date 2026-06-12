---
title: "how to make usb headset work in ubuntu 9.04"
date: 2009-06-11
forum: Multimedia Software
---

### Post by oenone on 2009-06-11
i have an A4tech hd-800 usb headset

how can i make it work on ubuntu 9.04?


so i can make voice chat , listen to musik etcc...

please help 

thanks

---

### Post by kostkon on 2009-06-12
Firstly, let's see if it is recognised. In a terminal
```
aplay -l
```
if you see it listed then you are fine.

Then, you'll need to install the *PulseAudio Device Chooser* utility from *Synaptic*. It will allow you to set a default output device (your headset, if you want) for your system, easily move the audio streams of the applications from your soundcard to your headset on-the-fly and vice-versa and some other things.

For more info check [this thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

---


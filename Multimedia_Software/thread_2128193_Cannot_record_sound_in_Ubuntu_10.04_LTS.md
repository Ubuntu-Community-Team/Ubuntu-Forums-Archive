---
title: "Cannot record sound in Ubuntu 10.04 LTS"
date: 2013-03-22
forum: Multimedia Software
---

### Post by pauls104 on 2013-03-22
Hi,

I'm using Ubuntu 10.04 LTS. I can hear sound perfectly fine, but I cannot record sound. When I go to "Sound Preferences" and then "Input", the only option I see is "Internal Audio Analog Stereo". I set the "Input Volume" to the maximum, but it still doesn't work. Any suggestions?

Thanks in advance.

---

### Post by tgalati4 on 2013-03-22
In a terminal, post the output of:

```
aplay -l
```

What are you using for a microphone?  Internal Audio Analog Stereo implies line-level signals--from a CD player.  Do you have a true microphone input or only a line-level input?  Try plugging in an mp3 player with a 3.5mm stereo jack and put the volume at 50% and record something.  If you get a decent recording, then you probably only have line-level inputs.

---

### Post by JonathanLloydMedia on 2013-03-22
> **tgalati4 said:**
> In a terminal, post the output of:

```
aplay -l
```

What are you using for a microphone?  Internal Audio Analog Stereo implies line-level signals--from a CD player.  Do you have a true microphone input or only a line-level input?  Try plugging in an mp3 player with a 3.5mm stereo jack and put the volume at 50% and record something.  If you get a decent recording, then you probably only have line-level inputs.



I agree, from all my experiences with Ubuntu, it's always come ready to record audio from a stock installation.  it sounds life a hardware issue. try also plugging in a USB web cam and see if you can get some audio recorded with that.  let us know if you figure it out so the knowledge can be passed on. good luck

---

### Post by ajgreeny on 2013-03-22
It is also worth opening alsamixer in terminal to see if "capture" is muted.  If there are two "M" showing at the bottom of the capture column use your M key to togle it and cursor keys to raise and lower the level.

---

### Post by pauls104 on 2013-03-22
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Oh, and when I use Windows 7 on the same laptop, I can record sound totally fine. I can just speak into the laptop.

---

### Post by pauls104 on 2013-03-24
Any suggestions on how to fix? I would be happy to provide additional information...

---

### Post by mörgæs on 2013-03-24
Are you sure that you want to struggle with the problem in 10.04, which has only one month left of support anyway? You could consider a clean install of 12.04 or 12.10 as a first step.

---


---
title: "record sound not through microphone"
date: 2010-10-07
forum: Multimedia Software
---

### Post by ahso4271 on 2010-10-07
Hi
recording defaults to my microphone but I want to record sounds directly from a application.
How? Many thanks
Michael

---

### Post by nothingspecial on 2010-10-07
```
sudo apt-get install pavucontrol
```Start running the recording app (sound recorder etc)

Go Applications > Sound and Video > Pulse audio volume control

Select the recording tab and  change "Internal Audio Analogue Stereo" to "Monitor of Internal Audio Analogue Stereo"

Now that application will be set to record internal sound, if you want to use it with a microphone again you will have to reverse the process.

[http://www.youtube.com/watch?v=VdjuH5Crbpk](http://www.youtube.com/watch?v=VdjuH5Crbpk)

---

### Post by Lifeis on 2010-10-07
Yeah, I would do what is suggested above.
Or have a look in the Software repository for Audio input selection software. Im sure there is one called 'Jake' or 'Jack' something, a whole load of audio applications one of which can select multiple audio inputs.
-Lifeis

---

### Post by ahso4271 on 2010-10-08
not such option within pulseaudio settings. I might even use alsa? previously on OpenSuse I had to remove pulse...
Cannot find any suitable jack as well...so i guess i install:
alsa-oss and see what happens? xvidcap uses dev/dsp....?
Thanks

---

### Post by ahso4271 on 2010-10-09
Well i can change it in pulse sound volume but only for recorditnow. Wich unfortunately gives sound not in sync with video. So I have to use xvidcap, cinellerra or ?
Many thanks
Michael

---


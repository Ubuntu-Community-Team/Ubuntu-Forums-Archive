---
title: "Is the sound quality of a Huge .flac differ than the splited one?"
date: 2015-10-04
forum: Multimedia Software
---

### Post by czgirb on 2015-10-04
Yesterday I download a zip file, which after an extract ... i will have **.accurip, .cue, .flac,** and **.log** file, the .flac is more than **280MB**.
 So, by using **Medieval CUE Splitter**, I split the file into several **small .flac** files.
When played by using **DeaDBeeF 0.6.2**, I think the sound is dull. So, I try to input the file directly from the original one.
And ... the sound is totally improved. Why?

---

### Post by czgirb on 2015-10-04
I often split the huge .flac or .wv file. But I never found there is any differences in sound quality.
But yesterday ... what I found is weird. and never founded before.
Just wanna know why this happen?
Thank you.

---

### Post by mc4man on 2015-10-04
With out the file in question no decent way to tell. Plus you are splitting the flac in windows, mac or maybe thru wine??,  have you tried using a linux cue splitter on that file?

---

### Post by czgirb on 2015-10-04
linux cue splitter ... just heard the name
How can I install it?

---

### Post by mc4man on 2015-10-04
There are numerous varitions of using shntool & cuetools but this works  quite well here & names, tags, ect.
[https://launchpad.net/~flacon/+archive/ubuntu/ppa](https://launchpad.net/~flacon/+archive/ubuntu/ppa)

Otherwise search out info on shntools/shnsplit, ect.

---

### Post by FakeOutdoorsman on 2015-10-05
Another method to split:
```
ffmpeg -i input.flac -f segment -segment_time 60 -c copy output_%03d.flac
```
See [FFmpeg segment muxer documentation](https://ffmpeg.org/ffmpeg-formats.html#segment_002c-stream_005fsegment_002c-ssegment) for more info.

You have several methods to choose from.

---

### Post by yoshii on 2015-10-05
Check your sound/output preferences settings in DeadBeeF.  Maybe you have selected the wrong thing.  Also check your output levels maybe you accidentally lowered the PCM level or something while boosting the Master output level or whatnot.

---

### Post by Rob Sayer on 2015-10-09
Well, according to this ...

[https://www.hydrogenaud.io/forums/index.php?showtopic=57563&st=0&p=683198&#entry683198](https://www.hydrogenaud.io/forums/index.php?showtopic=57563&st=0&p=683198&#entry683198)

... Medieval is pretty rubbish.  In theory splitting a flac file shouldn't cause problems but that doesn't mean it can't be messed up.

I've had good luck with cuetools etc.  This is a decent guide:

[http://danilodellaquila.com/blog/how-to-split-an-audio-.flac-file-using-ubuntu-linux](http://danilodellaquila.com/blog/how-to-split-an-audio-.flac-file-using-ubuntu-linux)

I

---


---
title: "Sound from ASUS P7131 My Cinema TV Tuner card"
date: 2009-06-26
forum: Multimedia Software
---

### Post by Dingo_aus on 2009-06-26
The Asus P7131 is a NXP (Phillips) saa7134 based Analogue TV Tuner card.

Whilst in 8.10 the saa7134 device modules are loaded automatically which gives video, audio can be any issue.

For the impatient, the necessary CLI command to execute each time before watching the video from the saa7134 is:

```
play -r 32000 -t ossdsp /dev/dsp1
```

**"play"**
The "play" command is part of the "sox" program, so you may have to install the sox package if you don't have it.

**"-r 32000" **
Sound is usually played at a rate of 48Khz samples.  The saa7134's digital output is at 32Khz so if you try to play it at 48khz you will get buffer underruns about every 0.5 seconds.  This option means the video and audio will sync.

**"-t ossdsp"**
This tells the play command to use format type "ossdsp" for the input.  If you get complaints about unknown file types then you should install the lidsox packages that contain the format you need.

**"/dev/dsp1"**
This is the file which is played. Effectively the saa7134 driver creates a second soundcard in you /dev/ directory. So by playing what is being sent to the second card (/dev/dsp1) to the first (/dev/dsp) you are mapping the second to the first.

Because the file known as /dev/dsp1 never returns and end of file condition, this command will never finish.

If you want to stop it, type Ctrl+C.

---


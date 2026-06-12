---
title: "screen recording with audio and video"
date: 2010-08-12
forum: Multimedia Software
---

### Post by kornelix on 2010-08-12
I want to do a screen capture with audio and video. I use Ubuntu 10.04 64-bit. 

I have now spend about half a day trying various tools, most of which seem to be half finished or abandoned. I have not found any usable docs for any of these.

gtk-recordmydesktop and xvidcap will both capture video, but seem unable to capture audio from a microphone. 

The mic is connected and the sound preferences "input" tab shows the input level jumping up when I speak, so it must be working.

I tried the pulse audio device chooser app to make sure the mic is selected, but the choices for input are DEFAULT and "other", which shows a blank input with no choices. 

xvidcap multi-frame dialog has dev/dsp pre-selected as the input device, with no other options. It does not work.

If I enable audio with gtk-recordmydesktop, it refuses to start and says it cannot open the sound card. There is no apparently no way to do this using the "advanced" dialog which has DEFAULT preselected as the audio input device and no other options. /dev/dsp also fails to start.

I spent some time searching google and the forums here, to no avail. So should I give up trying to do this with Linux or is there some obscure method I only need to discover?

I prefer xvidcap, since the ogg format output by recordmydesktop seems to be a write-only format. 

Please someone point me to a reasonable doc that explains how to do this. If you know that there is no such doc, then you can tell me to quit wasting my time.

---

### Post by ron999 on 2010-08-12
Hi
There's a tutorial here:-[http://ubuntuforums.org/showthread.php?t=1392026]("http://ubuntuforums.org/showthread.php?t=1392026")

---

### Post by kornelix on 2010-08-13
Thanks for the tip, ron999. 

The recipe suggested is very complex, would have to be repeated after every Ubuntu updgrade (6 months), would conflict with regular software updates, and is subject to technical changes at any time, invalidating the recipe. My need for having audio in my screencast is not urgent enough to warrant the hassle and risk, so I will give up for now and hope that the geeks in charge will clean up their act (xvidcap, recordmydesktop, pusleaudio, etc.).

---

### Post by williamts99 on 2010-09-20
In recordmydesktop, try changing Advanced>Sound>Device name from 'DEFAULT' to 'default'.

If you need to change what is being recorded, use pavucontrol
Install pavucontrol using ```
sudo apt-get install pavucontrol
```
Run pavucontrol and go to the recording tab **while recordmydesktop is actively recording** something, you will see an item called
"ALSA plug-in[recordmydesktop]:ALSA capture from"
If you want to record from the mic it should be something like 'Internal Audio analog Stereo', If you want to record everything that is coming out of your speakers choose 'Monitor of Internal Audio analog Stereo'.


Best Regards,
Will

---


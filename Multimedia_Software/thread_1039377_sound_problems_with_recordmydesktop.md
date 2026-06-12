---
title: "sound problems with recordmydesktop"
date: 2009-01-14
forum: Multimedia Software
---

### Post by wolfwood2x on 2009-01-14
Please note that I am NOT trying to record sound with a microphone. Please do not link to the skype video. 

I am trying to get sound recorded from the window application I am running. I have tried changing from Alsa to Pulse Audio and all that does is cause recordmydesktop to hang when encoding. I let it sit for 30 minutes on a 15 second video and it never moved from 0%

I have checked alsamixer and nothing is muted. I ran gtkrecordmydesktop and set sound to the Default device and it did not work at all.

What am I doing wrong?

---

### Post by markbuntu on 2009-01-14
Read this

[http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

---

### Post by andr3w on 2009-01-27
> **markbuntu said:**
> Read this

[http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

He is NOT trying to record from the microphone.
That video is for people trying to record from the microphone.

---

### Post by williamts99 on 2010-09-20
In recordmydesktop I changed the Advanced>Sound>Device name from DEFAULT to default. (not sure if this is needed)
Then I installed pavucontrol using ```
sudo apt-get install pavucontrol
```
Run pavucontrol and go to the recording tab **while recordmydesktop is actively recording** something, you will see an item called
'ALSA plug-in[recordmydesktop]:ALSA capture from'
You must change this to 'Monitor of Internal Audio Analog Stereo'

Best Regards,
Will

---


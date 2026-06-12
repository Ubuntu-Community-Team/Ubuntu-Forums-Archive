---
title: "Intel AC'97 Sound Problem"
date: 2011-10-25
forum: Multimedia Software
---

### Post by diedthreetimes on 2011-10-25
I just installed ubuntu 11 and my sound isn't working. More specifically if the sound is all the way up I can hear very faint noises.

I've read around and this seems to be a common problem historically, but none of the fixes are working for me. There appears to be a similar question already out [there](http://askubuntu.com/questions/33190/no-sound-on-a-realtek-ac97)

   ```
 
    $ aplay -l
    **** List of PLAYBACK Hardware Devices ****
    card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
      Subdevices: 1/1
      Subdevice #0: subdevice #0


    $ lspci | grep audio

    00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
```

I've ensured that my volume is up in alsamixer from [this](http://www.linuxquestions.org/questions/linux-hardware-18/sound-problems-intel-corp-82801eb-er-ich5-ich5r-ac97-audio-controller-rev-02-a-270323/)

I've also tried [the fix from the guide](http://ubuntuforums.org/showthread.php?t=14989&highlight=ac97_quirk&page=2), with no luck.

Furthermore I have tried to update to the newest alsa drivers, but also no luck. [This](http://tehpost.blogspot.com/2008/07/ubuntu-no-sound-using-intel-corporation.html) post from 2007 even suggested downgrading to a different kernel rev. I am tempted to try it, but there has got to be a better way. 

Please let me know if there is anymore information that I provide.

---


---
title: "Pulseaudio and Maudio Revolution 5.1 subwoofer problem"
date: 2009-09-04
forum: Multimedia Software
---

### Post by necklas on 2009-09-04
I'm using Ubuntu 9.04 (fresh installed, not upgraded) with a Maudio Revolution 5.1 soundcard with a 5.1 analog speaker setup. To get a 5.1 upmix for my stereo music I changed the default channel setup to 6 (as suggested here [http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)). Now I get sound out of all my speakers BUT

the subwoofer is mixed with the front-left as well as with the front-right channel! That means if I unplug my front speakers an run 
```
speaker-test -Dplug:surround51 -c6 -l1 -twav 

``` (as mentioned here [https://help.ubuntu.com/community/SurroundSound)]("https://help.ubuntu.com/community/SurroundSound") I can here the "front-left" and "front-right" through my subwoofer.
If I check the sound level of the different channels in pulseaudio manager, it seems as if the lfe channel isn't getting any signal. In alsamixer the front volume control adjusts the subwoofer as well.

Any ideas? Haven't found anything in the web and I'm pretty clueless.

---

### Post by necklas on 2009-09-05
Well, haven't figured out what the problem is but for now I'm using the .asoundrc file which I found here [http://ubuntuforums.org/showthread.php?t=400268&highlight=pulseaudio+audio+revolution](http://ubuntuforums.org/showthread.php?t=400268&highlight=pulseaudio+audio+revolution)

I switched my Music and Movie playback to ALSA (System -> Preferences -> Sound) and now the upmixing works fine. I haven't tried to play DVDs yet but I hope it works as well.

If anybody finds a solution to my actual problem just post it here. Would be great even so I'm happy as well with the ALSA workaround.

---


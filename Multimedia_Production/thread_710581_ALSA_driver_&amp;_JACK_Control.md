---
title: "ALSA driver &amp; JACK Control"
date: 2008-02-28
forum: Multimedia Production
---

### Post by drumanart on 2008-02-28
I use a DELTA 1010 sound card and I have problems with the ALSA- mixer and the JACK-control.

If I type in a terminal **aplay -l **I get the result:

card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 1: M1010 [M Audio Delta 1010], device 0: ICE1712 multi [ICE1712 multi] 
  Subdevices: 0/1 
  Subdevice #0: subdevice #0 

It seams that my sound card, a DELTA 1010 is recognized and ready for use.
But why is it not possible do adjust any volume in the ALSA mixer nor with Envy24 control. Both programs allow me to change channels and even mute them but the sliders don't work.
Trying now to configure JACK with the alsa driver the program gives error messages: 
**22:32:55.903 Could not connect to JACK server as client. Please check the messages window for more info.**
In JACK the only configuration what doesn't shows errors is with the oss driver and using  the dummy possibility. 
Some things works other not........
I'm very pleased for help thks

---

### Post by erginemr on 2008-02-29
There is a package "linux-backports-modules" that has the latest versions (or kernel patches) for sound cards. You may try to install this package to see if it helps:
```
sudo aptitude install linux-backports-modules
```

---

### Post by erginemr on 2008-03-01
You can also try this howto:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

You need to find the correct model of your card and add "snd-hda-intel model=<your_model>" into the file /etc/modprobe.d/alsa-base.

---


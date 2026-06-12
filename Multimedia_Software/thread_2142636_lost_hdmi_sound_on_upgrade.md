---
title: "lost hdmi sound on upgrade"
date: 2013-05-06
forum: Multimedia Software
---

### Post by slgtheindividual on 2013-05-06
upon upgrading to 13.04 from 12.10 the hdmi picture on my tv works fine but sound does not, it worked perfectly before, hdmi doesn't come up on the sound or pulseaudio menu, 


sudo aplay -l


gives


```
**** List of PLAYBACK Hardware Devices ****card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

I have tried 


sudo alsamixer -c 0


and then unmuted S/PDIF but nothing changes (also whenever I start a new session S/PDIF is once again muted)


also tried running 


speaker-test -c 2 -r 48000 -D hw:0,3


but again nothing happened. I have intel HD graphics 4000 and an i5 processor.


Thank you in advance for any help

---

### Post by LaptopU on 2013-05-06
I had this problem too.  I did:

```
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install oem-audio-hda-daily-dkms
```

This installs the daily updates and after I did that my HDMI device appeared, happy days.  Hope this works for you.

---

### Post by slgtheindividual on 2013-05-06
The first two commands work fine but then when I run ```
sudo apt-get install alsa-hda-dkms
``` I get the following:
```
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Unable to locate package alsa-hda-dkms
```

I rebooted but it still doesn't appear.

---

### Post by slgtheindividual on 2013-05-06
I also tried following the instructions here [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) but that also did not help and I still get Unable to locate package alsa-hda-dkms after an update and a reboot

---

### Post by pqwoerituytrueiwoq on 2013-05-06
sticky in general help, link so i don't repeat my self
[http://ubuntuforums.org/showthread.php?t=2141858](http://ubuntuforums.org/showthread.php?t=2141858)

---

### Post by LaptopU on 2013-05-06
Try

```
sudo apt-get install oem-audio-hda-daily-dkms
``` as the last line instead?  (Edited my original post accordingly).

---

### Post by slgtheindividual on 2013-05-06
Thank you very much, I updated to 3.9 kernal using the link provided in the sticky and now have sound =]

---

### Post by slgtheindividual on 2013-05-06
[COLOR=#000000]thanks again for everyone's help[/COLOR]

---

### Post by erikthedrink on 2013-05-08
cool.

---

### Post by Jeremy_Morris on 2013-08-21
I too have tried following this - I have upgraded kernel to 3.9.11-030911-generic, but all attempts to install oem-audio-hda-daily-dkms fail with an error that says there is a BUILD-EXCLUSIVE flag which appears to dislike my kernel version?
Any advice on how I fix this would be very much appreciated!

---


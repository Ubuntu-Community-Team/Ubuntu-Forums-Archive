---
title: "sound only from one side of the headphones"
date: 2010-05-05
forum: Multimedia Software
---

### Post by doctor who on 2010-05-05
after i installed 10.4 (at 9.10 it worked fine) i get sound only on the right of the headphones, used another headphone and same...
i would appreciate it if someone could direct me to a solution.
thanks from advance :) (sorry if there is already a thread about it, i have searched but nothing appear)

---

### Post by lidex on 2010-05-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by doctor who on 2010-05-06
```
Linux htpc 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux


**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Advanced Linux Sound Architecture Driver Version 1.0.21.


Codec: Analog Devices AD1986A

```

thanks allot :)

---

### Post by lidex on 2010-05-06
> **doctor who said:**
> [CODE]
uploaded a screenshot of the system monitor... if you need something else please be more specific,'cus i didn't get what you want.
thanks allot :)

That would be manufacturer and model number. Toshiba m30, for example.

---

### Post by doctor who on 2010-05-07
well... I really don't know that... is there a way i can find out? the box says SilverStone

---

### Post by lidex on 2010-05-08
Do "Part A" here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---


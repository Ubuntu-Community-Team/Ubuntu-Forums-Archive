---
title: "Very low sound | Tried lots of fixes"
date: 2010-05-27
forum: Multimedia Software
---

### Post by specialalaa on 2010-05-27
Hi. Sound is very, very low when I play mp3s or anything off youtube.com.. When the volume is at maximum I can barely hear the music if I really press the earphones into my ear....

I've opened up **alsamixer** and everything (Master, Headphone, Speaker, PCM) is at 100.. My audio card is installed and recognized correctly, because **aplay -l** shows me this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I already tried reinstalling the alsa-base and alsa-utils; nothing seems to fix this =(...

And by the way, the volume applet thing disappeared during removing/reinstalling things (although I can still hear the very, very low sound, and I can still control the volume with Fn+F3 and F4); I also installed an package called pavcontrol (read about it in old topics), but still nothings worked..

Useful information: Ubuntu 10.04 32-bit dual booting with Windows 7 64-bit.. The volume works perfectly fine in Windows..

Help me please =(

**EDIT:** I also tried connecting the laptop via HDMI, and no sound is heard as well..

---

### Post by Exterminator13 on 2010-05-28
I have the same problem! I tried everything too! Nothing helped!
My system is Kubuntu 10.04, base alsa drivers, audio codec ALC889A

PCM channel in KMix is set to 100% but sound in Flash player, SMPlayer and all those programs which use PulseAudio by default is much lower than in native KDE programs (Dragon Player, Amarok).

I feel the solution is very simple: to change config file or something.
The only clue is after I installed PulseAduio and uninstalled it sound became even lower! It means, sound level can be changed... but where?

---

### Post by Exterminator13 on 2010-05-28
specialalaa, maybe it will help you:
[http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)
from
[http://ubuntuforums.org/showthread.php?t=1480429](http://ubuntuforums.org/showthread.php?t=1480429)

and

[http://www.vampwarez.com/2010/05/linux-sound-problems-guide.html](http://www.vampwarez.com/2010/05/linux-sound-problems-guide.html)

The first didn't help me. I'll try the last one.

---

### Post by lidex on 2010-05-30
> **specialalaa said:**
> Hi. Sound is very, very low when I play mp3s or anything off youtube.com.. When the volume is at maximum I can barely hear the music if I really press the earphones into my ear....

I've opened up **alsamixer** and everything (Master, Headphone, Speaker, PCM) is at 100.. My audio card is installed and recognized correctly, because **aplay -l** shows me this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I already tried reinstalling the alsa-base and alsa-utils; nothing seems to fix this =(...

And by the way, the volume applet thing disappeared during removing/reinstalling things (although I can still hear the very, very low sound, and I can still control the volume with Fn+F3 and F4); I also installed an package called pavcontrol (read about it in old topics), but still nothings worked..

Useful information: Ubuntu 10.04 32-bit dual booting with Windows 7 64-bit.. The volume works perfectly fine in Windows..

Help me please =(

**EDIT:** I also tried connecting the laptop via HDMI, and no sound is heard as well..

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Exterminator13 on 2010-05-31
My system is Kubuntu 10.04 LTS AMD64.

In all the apps which have PulseAudio as native sound interface (SMPlayer, flash in browser) sound is significantly lower than in native Phonon apps is... (like Amarok or Dragon Player)

I opened kmix. PCM channel is set it to 100%. alsamixer from command-line showed all the sliders are set to 100%. I installed/uninstalled pulse audio server and its pavuchooser. Didn't help. Sound became even lower in all Gnome apps.

I tried python-script alsa utility for low-level soundcard tuning - didn't found something useful: Analog Audio output has not any tuning sliders... :(

My system config:
```
oleg@comp:~/Downloads$ uname -a
Linux comp 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
oleg@comp:~/Downloads$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
oleg@comp:~/Downloads$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 29 2010 for kernel 2.6.32-22-generic (SMP).
oleg@comp:~/Downloads$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC889A
```

---


---
title: "No sound in lucid After alsa upgrade"
date: 2010-07-15
forum: Multimedia Software
---

### Post by sleepee on 2010-07-15
So i upgraded to 10.04 a few months ago, right after it was released.  clean install.   it worked perfectly out of the box, or so it seemed.  I had had sound problems in 9.10 that i didn't experience after i upgraded... until i tried to use some headphones a few days ago.
when i connected the headphones, the speakers wouldn't mute.  i thought it was no big deal.  i had the same issue in 9.10 and it was fixed after i upgraded alsa.  i figured i'd try the same thing.
I used the same alsa upgrade script i used last time ([http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)) and it fixed the jack sensing and the sound worked perfectly... for about 5 minutes.  after a short while of playing audio, sound would stop playing.  i'd stop getting sound from video files, audio files, and even from my browser.  i'd have to reboot to get sound again... only to lose it again in about 10 minutes.
Now it's regressed to the point where i have no sound even after i reboot.

weird thing is, when i test out an audio file with aplay, it works... even if i just get garbage sound from some mp3 files.

anyway, i've got an HP dv7 and this is my aplay -l output

```
sleepee@sleepee-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```any ideas??

---

### Post by sleepee on 2010-07-15
never mind... i figured what the problem was... i think.
it seems like after i did the alsa upgrade, the settings in pulse audio's volume control weren't configured right... after some tinkering with the settings, the sound works fine....
sorry for wasting a thread on that lol!!

---

### Post by Yellow Pasque on 2010-07-15
It's okay if you mark it SOLVED ;)
It's good to know the problem wasn't the script.

---


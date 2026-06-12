---
title: "cannot open mixer: No such file or directory"
date: 2015-05-26
forum: Multimedia Software
---

### Post by Yachint on 2015-05-26
I have tried Numerous attempts to open alsamixer which includes:
```
 sudo apt-get remove --purge alsa-utils
```
```
sudo apt-get install alsa-utils
```
and many other ways but it doesn't find the file or directory. My main problem is that I could not get my audio to work. I tried using these commands in the terminal:
```
yachint@yachint-B85M-D3H:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```


 to see if ubuntu detects the sound card or not and it shows it there but when I try to play any audio there is no sound even though I have maximized it and added myself in the audio group. That is why I need alsamixer to work so I can try and adjust it from there.
I am completely new to Linux and I have no Idea what to do next so I need some urgent help. 
And if you are wondering if have I checked other forums or not, believe me I have checked them multiple times and still I can't find a solution.
Thanks in advance.

---


---
title: "Sound issues alsa/oss in NB205"
date: 2009-12-18
forum: Multimedia Software
---

### Post by BretFTW on 2009-12-18
Okay so I am fairly new to linux, I played with a couple distros years ago, but never actually used it as my primary OS. I hate windows 7 on this netbook so much that I decided to switch to ubuntu.

Now of course I am having problems with sound on the NB205. Before I actually installed it, I did get sound to work by removing alsa, and putting on OSS. The only problem I have is getting system sounds to work. I am trying to follow the instructions listed here:
[URL="https://help.ubuntu.com/community/OpenSound"]
https://help.ubuntu.com/community/OpenSound[/URL]

This is the step where I run into trouble of course

> 
Configure ALSA Apps to Use OSS (OPTIONAL) 
In general, it's better to have applications use the OSS API or a higher level sound API/library with OSS4, but if you have the libasound2-plugins package (it's pre-installed on standard Ubuntu installs), it is possible to have ALSA applications output to OSS with [this workaround]("http://www.opensound.com/wiki/index.php/Tips_And_Tricks#ALSA_Emulation") (the first method). The workaround states
> **ALSA Emulation **

 
[LIST]
[*]There are two main methods to achieve this:
[LIST]
[*]libasound2's pcm-oss plugin:
[LIST]
[*] Easiest method, but will not work with all programs. It works by making libasound use OSS via the pcm-oss plugin.
[*] First, install the pcm-oss plugin. It is included in the alsa-plugins distribution.
[LIST]
[*] Debian: install libasound2-plugins package.
[/LIST]
 
[*] Make sure an ~/.asoundrc file exists. It should contain the lines below:
[/LIST]
 
[/LIST]
 
[/LIST]
 ```
 pcm.!default
 {
   type oss
   device /dev/dsp
 }
 mixer.!default
 {
   type oss
   device /dev/dsp
 }
```This is where I go okay "Okay WHAT am I supposed to do!?" 

I am totally lost. If someone could help me out or guide me in some way it would be greatly appreciated.

Thanks,
Bret

---


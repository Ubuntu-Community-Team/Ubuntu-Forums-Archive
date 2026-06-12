---
title: "Videos lag after resuming from suspend"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by aashay on 2008-01-26
I finally got suspend to work properly on my laptop. Now the only problem is after resuming from a suspend, videos played in everything except vlc (totem, mplayer, flash movies in firefox etc) lag. The frame rate starts at about 5fps and goes slowing down till the video comes to a standstill. Seeking the video again resumes it at 5fps. This happens irrespective of whether compiz is running or not. I couldn't think of any other explanation. Does anyone have any idea what could be causing this?

EDIT: I wrongly assumed it was the video when audio is the real culprit. Its the same deal with audio files as well. My dmesg is filled with such messages:

[ 3233.028000] hdaudio: RIRB timeout (cad=0, nid=7, d=0, verb=f0d, parm=0)
[ 3233.648000] hdaudio: RIRB timeout (cad=0, nid=2, d=0, verb=f0d, parm=0)
[ 3236.580000] hdaudio: RIRB timeout (cad=0, nid=7, d=0, verb=f0d, parm=0)
[ 3237.200000] hdaudio: RIRB timeout (cad=0, nid=2, d=0, verb=f0d, parm=0)
[ 3238.264000] osscore: Output timed out on audio engine 6/'Intel HD Audio speaker (VMIX0)' (count=0)
[ 3239.268000] osscore: Output timed out on audio engine 6/'Intel HD Audio speaker (VMIX0)' (count=0)
[ 3240.288000] osscore: Output timed out on audio engine 6/'Intel HD Audio speaker (VMIX0)' (count=0)
[ 3241.304000] osscore: Output timed out on audio engine 6/'Intel HD Audio speaker (VMIX0)' (count=0)

I tried rmmod to try to remove and re-add the modules. This is what I get: 

aashay@kriz-jr:~$ sudo rmmod vmix ossusb hdaudio osscore
ERROR: Module vmix is in use
ERROR: Module ossusb is in use
ERROR: Module hdaudio is in use
ERROR: Module osscore is in use by vmix,ossusb,hdaudio

---

### Post by aashay on 2008-01-26
Alright... I figured it out. I need to run
```
sudo soundoff
sudo soundon
```
to get sound working again. How do I automate this??

---

### Post by alexei.colin on 2008-02-09
> **aashay said:**
>  How do I automate this??

I don't know anything about this problem, but I did have to automate commands to happen upon each suspend and resume. It can be done by creating shell scripts in the directories: /etc/acpi/suspend.d and /etc/acpi/resume.d

The directories contain scripts by default, so you can look at them for examples. Number in the filename specifies the order of execution. Also, don't forget to make the script you write executable: sudo chmod +x myscript.sh

Hope this helps.

---


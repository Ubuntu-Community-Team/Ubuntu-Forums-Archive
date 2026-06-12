---
title: "no sound in Ubuntu 18.04"
date: 2019-08-17
forum: Multimedia Software
---

### Post by raymondvillain on 2019-08-17
Running dual boot Gigabyte motherboard (AORUS X570), AMD Ryzen 5 3600x, RADEON graphics card, 64 Gbyte ram.  Sound works fine in Windows 10.  Booting to Ubuntu 18.04 there is no sound.  If I open Settings>sound>output tab  I am presented with 3 choices:  HDMI/DisplayPort-HD-Audio Generic, Digital OUtput (S/PDIF) -HD-Audio Generic, and Line Out - HD-Audio Generic.  The "test speakers" in all of these choices does not produce sound.  But if I select "Digital Output (S/PDIF) - HD-Audio Generic" and select the "Sound Effects" tab I can produce sound by clicking on any of the "alert sounds".  Weird.

I've tried several things.  Output of Alsamixer (in a terminal window) is not correct, screenshot:[IMG]file:///home/daddy/Pictures/Screenshot from 2019-08-17 10-48-55.png[/IMG]

Removed and re-installed Alsa, installed PAVUctrl, etc.  Don't know what to try next.  The output of  ```
sudo lspci -v.txt
``` is too large to attach, ```
lspci
``` is attached.

What to try next?
Any and all suggestions greatly appreciated.

---

### Post by pflarini on 2019-11-18
Hi Raymond, have you got this to work ?

---


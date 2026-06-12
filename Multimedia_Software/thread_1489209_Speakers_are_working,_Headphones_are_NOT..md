---
title: "Speakers are working, Headphones are NOT."
date: 2010-05-20
forum: Multimedia Software
---

### Post by zeddaybob on 2010-05-20
Audo is working fine through the Internal laptop speakers. when i plug in my headphones, nothing happens, the audio continues to play through the speakers, and nothing comes from the headphones. ive tried changing up things in sound preferences and alsa-mixer, but nothing seems to be working. 

Im 100% sure the head phone jack isn't broken, and the headphones aren't broken (they both work in windows just fine.)

Im running 10.04, on an amd-64x HP-dv3.
any help would be appreciated, i'll run codes in Terminal if you need me to. thanks

---

### Post by zeddaybob on 2010-05-20
[SIZE=2]okay i kinda switched things around here by adding "[/SIZE]options snd-hda-amd model=hp" to alsa-base.conf. but now only headphones work and not internal speakers. how to i get both to work properly?

---

### Post by WinterRain on 2010-05-21
See [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424") thread. Posts 28 & 29 seem to address the issue best.

---

### Post by lidex on 2010-05-21
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

### Post by vishudh on 2010-11-05
I had the same problem with my Toshiba satellite c650 laptop. But with the help from this link [URL=]http://www.youtube.com/watch?v=uOTKbrPkd94
[/URL] I added > options snd-hda-intel model=ideapad to /etc/modprobe.d/alsa-base.conf file. Now my headphones and speakers are working perfect.

---

### Post by rikkety on 2010-11-11
please am having the same problem
but i use a packard bell easynote mz36

---


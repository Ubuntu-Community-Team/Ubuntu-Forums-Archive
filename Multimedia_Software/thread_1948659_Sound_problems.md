---
title: "Sound problems"
date: 2012-03-28
forum: Multimedia Software
---

### Post by Curzey on 2012-03-28
Hello ubuntu pro's!

I got this problem on my ubuntu computer. It's a MSI GTX660. It got a sound system called Dynaudio. It has 2 speakers and a subwoofer.
Problem is it only plays sound from the subwoofer, not the speakers??

I've tried to follow this: [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

problem at that guide is: I get told to install the linux-audio-module which matches the kernel i have. I have kernel 3.0.0-17-generic (found by (uname -r)), and when i go into synaptics, i can only find 3.0.0-14 and 15-generic? I've also tried the Terminal way, dosnt work either?

I've also checked the alsa mixer, the speakers aint muted!!

I use the 32bit version of Ubuntu. It's dualbooted from win7 by wubi.exe.

Please help me mates):P

---

### Post by Yellow Pasque on 2012-03-28
More info, please: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Curzey on 2012-03-29
Hey  thank you for responding. SOrry i forgot some details!!!

Here it is [http://www.alsa-project.org/db/?f=6c4dfd8bf39fda20738bc3136641fa6716b4100c](http://www.alsa-project.org/db/?f=6c4dfd8bf39fda20738bc3136641fa6716b4100c)

---

### Post by Yellow Pasque on 2012-03-29
Add this line to /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=targa-8ch-dig
```
Hopefully, it works on next boot.

Taken from: [http://ubuntuforums.org/showthread.php?t=1702376](http://ubuntuforums.org/showthread.php?t=1702376)

---

### Post by Curzey on 2012-03-30
Hello again Temujin, it didnt work, but it actually did something :D Now no sound at all works!

Got this picture of my alsa mixer how it looks after that command. Hope that can help ya

---

### Post by Curzey on 2012-03-30
I looked at the guide u took the other command from... I followed the later part about the soundfix "script". Now it again just plays from subwoofer

---

### Post by Curzey on 2012-04-11
Bump!

---

### Post by saucysoup on 2012-06-07
Also experiencing this same issue (Dell Inspiron 9300).

---


---
title: "How to downgrade ALSA"
date: 2010-12-15
forum: Multimedia Software
---

### Post by roobinatube on 2010-12-15
Hi,

I have a lenovo G555, and there are plenty of forum posts complaining about the headphones not playing or muting speakers etc.

I found two fixes for this issue in ubuntu 10.04.

1) [http://www.uluga.ubuntuforums.org/showpost.php?p=9906171&postcount=24](http://www.uluga.ubuntuforums.org/showpost.php?p=9906171&postcount=24) 
This uses the linuxant conexant drivers, which worked, but made my internal mic sound fuzzy...

2) [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1043568&page=16](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1043568&page=16)
This requires no changes to ALSA, and works like a beauty... 

THE PROBLEM IS......!
upgrading to maverik screwed both these solutions up! The first one because the conexant drivers will not compile on the new kernel, the second because ALSA 1.0.23 uses cx20585 rather than conexant 5069 to control my sound. cx20585 solves the headphone issue but doesnt work with the microphone.

Why dont I just stick with 10.04? I have with kubuntu... however there are times when I need to extend the battery life and use lubuntu, but lubuntu dont give a download link for 10.04 anymore!

**How can I downgrade to ALSA 1.0.21 on lubuntu 10.10?**

Many thanks
Roo

---

### Post by roobinatube on 2010-12-16
bump... help please!

---


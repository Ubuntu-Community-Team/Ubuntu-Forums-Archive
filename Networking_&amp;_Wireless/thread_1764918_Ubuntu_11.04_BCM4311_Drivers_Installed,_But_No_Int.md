---
title: "Ubuntu 11.04 BCM4311 Drivers Installed, But No Internet"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by ajm113 on 2011-05-22
Hello, I installed Ubuntu 11.04 on my mom's Inspiron 1521 and before I had it on there I had a older version of ubuntu which worked fine and could connect to the Internet, but since my mother isn't that well educated in computers and wants a simple to use UI, Ubuntu came into mind.

Well after installing ubuntu for a hour or two and trying to configure the drivers to allow Internet access with out a USB adapter using the BCM4311 I tried everything such as following the pretty basic tutorials online on installing the drivers with no luck. I check the additional drivers application and it's telling me the drivers are installed properly and are okay. ... Well, why am I not able to find a list of wifi connections yet?

I did the update command and updated every package on the machine.

I reinstalled the kernal drivers for the BCM4311.

I even installed the installer for the kernal device and nothing seems to be working.

I will say this I am a ubuntu newbie still and I'm not too familiar on where everything is, so I may ask some low level questions. ;)

I would appreciate any help I can receive on this issue and thank you for reading.

---

### Post by bkratz on 2011-05-22
You might look at this

[http://ubuntuforums.org/showthread.php?t=1745437](http://ubuntuforums.org/showthread.php?t=1745437)

---

### Post by chili555 on 2011-05-22
I think bkratz also wants to see two terminal commands:```
rfkill list all
lsmod | grep dell
```

---

### Post by ajm113 on 2011-05-22
Sweet! Thank you soo much! That link worked perfectly!! :)


Thanks again!

-ajm

---

### Post by bkratz on 2011-05-22
Congratulations, and enjoy

---


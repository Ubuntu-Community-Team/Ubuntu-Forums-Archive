---
title: "nvidia drivers Ubuntu 7.04"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by instinctius on 2007-08-19
[I][FONT="Georgia"]hello over there!!!
hope u r all ok people ..
i m running a dual boot pc with XP and Ubuntu 7.04 
i have an nvidia 7600gs and id like to install the drivers ..
however when i checked on hardware information i saw that Ubuntu recognises my graphics card ..the thing is: how can i understand if the drivers are installed properly since i didnt do anythin!i just found my gforce there ...i mean that since i found my graphics card listed under the harware information tab, that means that is installed???
furthermore when i go to restricted drivers tab it says: nvidia accelerated graphics card driver - enabled - not in use.
in case its not properly installed, can u also give me a link to a guide???
thanks in advance ...

Akis ..[/FONT][/I]

---

### Post by tseliot on 2007-08-19
1) Can't you enable the driver from the Restricted Drivers Manager?
2) post the output of this command:
```
glxinfo
```
3) Here's a guide:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by instinctius on 2007-08-19
the thing is ..if i enable the driver from the restricted drivers tab ..that means that my card is fully coreectly installed???should i follow another way???is there a link to a guide???
thanksss

---

### Post by tseliot on 2007-08-19
> **instinctius said:**
> the thing is ..if i enable the driver from the restricted drivers tab ..that means that my card is fully coreectly installed???
You have to enable the driver from there. Then the application will tell you what to do next (e.g. restart your computer)

> **instinctius said:**
> should i follow another way???is there a link to a guide???
again:
[http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126)

---

### Post by instinctius on 2007-08-19
i have an nvidia g-force 7600 gs ..i can find it in both lists that are in ur guide ..which of 2 generic drivers must use??? i downloaded from nvidia: NVIDIA-Linux-x86-100.14.11-pkg1.run ..im complicated in the part concerning the generic drivers ..which one to choose ..any help??? :(

thank you in advance ..

Akis ..

---

### Post by tseliot on 2007-08-19
> **instinctius said:**
> i have an nvidia g-force 7600 gs ..i can find it in both lists that are in ur guide ..which of 2 generic drivers must use???
Go with the latest driver (nvidia-glx-new)

[QUOTE=instinctius;3215709]i downloaded from nvidia: NVIDIA-Linux-x86-100.14.11-pkg1.run ..im complicated in the part concerning the generic drivers ..which one to choose ..any help???
There is no need to install the driver from Nvidia's website. Method 1 of my guide should be good enough.

---

### Post by instinctius on 2007-08-19
i will follow method no1 ..but which generic driver i must use coz u say that i have to choose the correct one from the lists ..i find 3-4 times my card in both lists ..which one i should download in order to use???
thank uuu

---

### Post by tseliot on 2007-08-19
When you arrive at point 3 of Method 1 of the [guide]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1") you will have to choose the driver you need.

As I said before you should select nvidia-glx-new. Please read the guide carefully and do only what the guide suggests.

---

### Post by instinctius on 2007-08-19
ok ..there is a last tiny problem ..
the architecture of my kernel is: 2.6.20-16-generic
when im trying to install the dummy package it says that: couldnt find package linux-2.6.20-16-generic ...
any suggestions????

thanks in advance ...

Akis ..

---

### Post by tseliot on 2007-08-20
> **instinctius said:**
> ok ..there is a last tiny problem ..
the architecture of my kernel is: 2.6.20-16-generic
when im trying to install the dummy package it says that: couldnt find package linux-2.6.20-16-generic ...
any suggestions????

thanks in advance ...

Akis ..

try with "linux-generic"

---


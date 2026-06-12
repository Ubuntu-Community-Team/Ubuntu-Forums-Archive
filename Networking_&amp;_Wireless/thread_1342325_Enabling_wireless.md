---
title: "Enabling wireless"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by raucous on 2009-11-30
I'm running 9.04 and my wireless is not working. The option is greyed out and it says that wireless is disabled. I can get online just fine if I'm plugged in though. 

I've attached the info that Gnusci recommended I post ([http://ubuntuforums.org/showthread.php?p=6183681);](http://ubuntuforums.org/showthread.php?p=6183681);) it's a bit of a novella. So basically what I need to do is enable wireless and I hope that this info will help. Thanks in advance for looking this over.

---

### Post by chili555 on 2009-11-30
Here is the whole answer:> [   20.612104] iwl3945: Radio Frequency Kill Switch is On: 
[   20.612107] Kill switch must be turned off for wireless networking to work. 
Find the hardware wireless switch, flip it to 'on' and you should be all set. Network Manager will use your wired connection first, so disconnect the wire before you try the wireless.

---

### Post by raucous on 2009-11-30
Man i hit that button a million times and nothing happened. I spoke with a guy at a PC shop and he said that button was unimportant with ubuntu (whatever). so i hit it again and now it works.

---


---
title: "Wireless Problems in Ubuntu 11.04"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by beetleman64 on 2011-04-03
I'm using a Fujitsu-Siemens Amilo Li 2727 which is a laptop where you have to press Fn+F1 in order to turn the wireless on. This has never worked, although the past couple of releases have turned the wireless on automatically and earlier releases had a module called acerhk which worked.

The upgrade to 11.04 Beta has broken this, and poking around online shows it seems to be a result of a recent kernel upgrade. Does anyone have a fix, as the laptop is currently my only PC since my desktop went kaput.

Thanks in advance.

edit: I'd like to keep command line work to a minimum, and any massively complex fixes will make me a Fedora user (again).
edit2: The acerhk module didn't work, which is why I'm fairly desperate.

---

### Post by mx18bp on 2011-05-09
Exactly the same problem here, tried to fiddle around with backports but no solution found yet...

---

### Post by Rankin1 on 2011-07-07
Yep same here, tried using backports as well but failed miserably. Slightly/Very frustrating :(

---

### Post by praseodym on 2011-08-27
Hi folks. Try to activate the wireless via kill switch module:

```
sudo modprobe -v fsam7400 radio=1
```

---


---
title: "Logtech G35 Headset"
date: 2009-06-12
forum: Multimedia Software
---

### Post by ExplicitViper on 2009-06-12
i am getting sound out of my microphone, and i can hear whatever i say into it through the headset. i cant however hear the startup sound, or any other sounds. any suggestions?

---

### Post by ntom-taylor on 2010-02-08
I have the logic G35 headset (awesome) and can confirm this works fine out the box, no work needed on ubuntu 9.10.

Simply go to Sound -> Preferences and set it as your audio device under hardware and output.

uname -a
```
Linux version 2.6.24-24-server (buildd@yellow) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Fri Jul 24 22:44:54 UTC 2009
```

lsb_release -a
```
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.3 LTS
Release:	8.04
Codename:	hardy

```


/proc/cpuinfo
```
processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 104
model name	: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
```


Hope this helps others.

---


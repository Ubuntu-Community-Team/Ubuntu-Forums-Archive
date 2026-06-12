---
title: "Audio: no bass and delays (Acer 4820TG, ubuntu 10.10)"
date: 2010-11-25
forum: Multimedia Software
---

### Post by fuligginoso on 2010-11-25
OS: Ubuntu 10.10 Desktop Edition
Computer: Laptop Acer Aspire Timeline X 4820TG
Sound Card: don't know (how/where to check?)
Software tried: totem, vlc, rhythmbox (does not depend on software)
Output: headset and speakers (does not depend on output)
**The problem: Bass cannot be heard, and "part" of the music plays with a small delay ("offbeat") with respect to the "rest".**
Note: I have it dual-boot with Windows 7, where the audio works without problems.

Hi there, this is the first question I post. I hope this information is specific enough, otherwise I'll need some help on audio terminology. Thank you in advance.

---

### Post by lidex on 2010-11-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by fuligginoso on 2010-11-30
Thank you, here's the info:

[http://www.alsa-project.org/db/?f=b091c94b395af212c29a8b103047c875d41165e9](http://www.alsa-project.org/db/?f=b091c94b395af212c29a8b103047c875d41165e9)

cool tool btw.

---

### Post by lidex on 2010-11-30
Seems a bios update may be in order. Reference here:
[http://www.linlap.com/wiki/acer+aspire+4820+timelinex](http://www.linlap.com/wiki/acer+aspire+4820+timelinex)

---

### Post by fuligginoso on 2010-12-02
Hey, it went ok all by itself! Might be because of some security updates which my os made last week (?). Anyway, thanks for the help, now it works lika charm.

My linux love has started :)

---

### Post by lidex on 2010-12-02
> **fuligginoso said:**
> Hey, it went ok all by itself! Might be because of some security updates which my os made last week (?). Anyway, thanks for the help, now it works lika charm.

My linux love has started :)
You may have issues with random loss of sound. If that occurs try restarting alsa:
```
sudo alsa force-reload
```

---


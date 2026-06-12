---
title: "Hauppauge HVR 1110 IR Remote not found"
date: 2010-08-21
forum: Mythbuntu
---

### Post by Tobbs on 2010-08-21
I need help getting the IR-remote to work. 
I'm using MythBuntu 10.04.

Currently, the only sign of the IR bit I've seen is in dmesg:
```
tobias@mythix:/etc/lirc$ sudo dmesg |grep " IR "
[sudo] password for tobias: 
[   13.657172] tveeprom 1-0050: has radio, has IR receiver, has no IR transmitter

```

I can't find any devices in /dev related to IR.

---


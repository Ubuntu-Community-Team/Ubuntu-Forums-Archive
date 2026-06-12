---
title: "OSS4 no sound with SB X-FI"
date: 2008-09-19
forum: Multimedia Software
---

### Post by boblemur on 2008-09-19
Hey all, im having problems with my sound card, its a Sound Blaster X-FI (not the old audigy one, but the new one, however i dont know exactly what model because SB have such a bad naming scheme)

```
osstest 
```
gives:
```

/dev/oss/oss_sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi (UAA) output
Note! Device is in use (by PID 7191/esd) but will try anyway
- Performing audio playback test... /dev/oss/oss_sbxfi0/pcm0: Device or resource busy
The device is busy. There is some other application
using it.
Can't open the device


```

so i ran:
```
killall esd
```
then:
```
osstest
```
and got:
```
/dev/oss/oss_sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi (UAA) output
- Performing audio playback test... 
  <left> Device returned error: Input/output error
```

so my sound card is recognized however i don't know what to do about io error...

thanks for any help in advance

---


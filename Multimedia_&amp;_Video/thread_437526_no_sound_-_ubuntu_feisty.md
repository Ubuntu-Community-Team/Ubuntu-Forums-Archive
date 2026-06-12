---
title: "no sound - ubuntu feisty"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by md5hash on 2007-05-08
yesterday i can hear sounds from my pc but after i restarted it was all gone.. heres what i got after typing aplay -l

```
feisty@feisty:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 2/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: YMF724F [Yamaha DS-1 (YMF724F)], device 0: YMFPCI [YMFPCI]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: YMF724F [Yamaha DS-1 (YMF724F)], device 1: YMFPCI - IEC958 [YMFPCI - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: YMF724F [Yamaha DS-1 (YMF724F)], device 2: YMFPCI - Rear [YMFPCI - Rear PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by spin2cool on 2007-05-08
Walk through this guide:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by md5hash on 2007-05-08
i did follow the steps but its not working....

---

### Post by md5hash on 2007-05-09
i remember yesterday there was a sound then i installed amarok then i uninstall it later after rebooting sound was gone... help please

---

### Post by trotur on 2007-05-09
> **md5hash said:**
> yesterday i can hear sounds from my pc but after i restarted it was all gone..

You'll have to force the order of your two soundcards, because their order may swap in every reboot.

There are two ways to do that:

1) Just yesterday I found this: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_soundcard](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_soundcard)
> **How to change default soundcard**
    * View available soundcards 
```
sudo asoundconf list
```
    * You should get something like this 
```
Names of available sound cards:
  Live
  V8237
```
    * Switch soundcard with 'example' being the name of the preferred soundcard 
```
sudo asoundconf set-default-card example
```
I guess you should use "YMF724F" (or similar that you get from list) as "example" above.

2) (alternative) See post [http://ubuntuforums.org/showthread.php?p=2593038](http://ubuntuforums.org/showthread.php?p=2593038) and adapt it to your situation.

I have used method 2) (I didn't know about 1)). I think it's better to use method 1) if it works properly.

---

### Post by analyticalman on 2007-05-17
Awesome - method 1 worked a treat on my new Ubuntu Studio 7.04 install.  Thanks man

---

### Post by md5hash on 2007-05-17
Thanks trotur.. its working now

---


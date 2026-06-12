---
title: "recordmydesktop - sound devices"
date: 2010-01-31
forum: Multimedia Software
---

### Post by cprofitt on 2010-01-31
If you want to find out what device to list for recordmydesktop you can use the following command:

arecord -l

This will yield a result that looks like this:

```

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
card 1: CinemaTM [Microsoft® LifeCam Cinema(TM)], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: U0x46d0x8b6 [USB Device 0x46d:0x8b6], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

To use the Microsoft LifeCam you would input hw:1,0 to the sound device. To use the other USB audio device you would use hw:2,0

---

### Post by hesjnet on 2010-04-02
Thanks for you advice but this sadly doesnt work for me

```
pal@pal-laptop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: U0x46d0x8c6 [USB Device 0x46d:0x8c6], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
pal@pal-laptop:~$ 


```

I want it to record the sound from my computer, not a microphone. Tried to set it as hw:0,0 but it didn't work.

Do you know what to do? Thanks!

---


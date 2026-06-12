---
title: "Ubuntu 12.10 - Tascam US-122 problems"
date: 2013-02-03
forum: Multimedia Software
---

### Post by eboats on 2013-02-03
Hello, I'm trying to get my Tascam US-122 Audio interface working with Ubuntu 12.10 on my new Dell Inspiron 3520 (64 bit) laptop and am having problems.  I followed the steps at :

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

I can get the Tascam light to show Green but I can't get any sound out of it (I have the Tascam audio outs going to my mixer and want to play back music from my music software).  When I go to System Settings/Sound, I do see the US-122 in the Output tab (though have to unplug/re-plug in the usb cable in order for it to show up).  So, I'd expect that because it shows up in the Output tab, that'd I'd be able to get some sound, but no luck.  

When I do a   cat /proc/asound/cards   I see the card :

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7d00000 irq 44
 1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 001/013)

I was able to get this Tascam US-122 working with an older version of Ubuntu.

Any idea how to troubleshoot/fix the issue?

---

### Post by unstrangeness on 2013-11-09
Hi,

I have pretty much the same problem. Did you get it to work somehow?

I'm pretty new to Linux and I run Ubuntu 12.04 LTS (64bit).

I followed the steps from this [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122) and this [http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122) page. The Tascam US-122 green LED lights up, but I can't get any input/output from it :(.

```
lsusb
``` gives me:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 003: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 002 Device 004: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 001 Device 010: ID 1604:8007 Tascam US-122 Audio/Midi Interface
```

where the Device number (10) increases with every time I unplug it and plug it in again

```
aplay -l
``` gives me

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272X Digital [ALC272X Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: USX2Y [TASCAM US-X2Y], device 0: US-X2Y Audio [US-X2Y Audio #0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
elokuu@elokuu-EasyNote-TJ75:~$ 
```

```
arecord -l
``` gives me

```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: USX2Y [TASCAM US-X2Y], device 0: US-X2Y Audio [US-X2Y Audio #0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

for ```
cat /proc/asound/cards
``` i get

```
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0600000 irq 43
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xcfedc000 irq 44
 2 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 001/010)

```

In *System Settings --> Sound* I can see the Tascam in the *Output* and* Input* tab as: *Analog Output US-122 Audio/Midi Interface* and *Analog Input US-122 Audio/Midi Interface*

When I run *Audacity* or *Pure Data* I can choose the Tascam as *Output* and*/or Input* device, but it doesn't work.

Pure data shows me:

[IMG]http://s7.postimg.org/i9ul0uuij/image.png[/IMG]

And Audacity get stuck in the recording after a few millisecond and when I have set the Tascam as playback device it says: *Error while opening sound device. Please check the output device settings and the project sample rate.*

Any idea how to fix this problem? Do I have to configure the Tascam somehow?

Thanks

---


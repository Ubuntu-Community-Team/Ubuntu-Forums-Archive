---
title: "Where do I find DVB au8522 xc5000 diver source and compile?"
date: 2012-06-08
forum: Multimedia Software
---

### Post by fixitdude on 2012-06-08
Where do I find the latest DVB au8522 xc5000 diver source code files and compile and install them?

I would like to try the latest drivers and see if they work, these two are the ones that work with my Hauppauge HVR950Q USB receiver.

They are part of the distro, but I'll be darned if I can find the source files.

I would hope that even though I am not running the latest Ubuntu, I should be able to use the source to compile and install the latest version, or maybe one previous version.

```

[4734544.736374] au0828: i2c bus registered
[4734545.026675] tveeprom 5-0050: Hauppauge model 72241, rev D3F0, serial# 6403338
[4734545.026681] tveeprom 5-0050: MAC address is 00-0D-FE-61-B5-0A
[4734545.026686] tveeprom 5-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[4734545.026690] tveeprom 5-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[4734545.026694] tveeprom 5-0050: audio processor is AU8522 (idx 44)
[4734545.026698] tveeprom 5-0050: decoder processor is AU8522 (idx 42)
[4734545.026701] tveeprom 5-0050: has no radio
[4734545.026704] hauppauge_eeprom: hauppauge eeprom: model=72241
[4734545.063622] au8522 5-0047: creating new instance
[4734545.063626] au8522_decoder creating new instance...
[4734545.068849] tuner 5-0061: chip found @ 0xc2 (au0828)
[4734545.105357] xc5000 5-0061: creating new instance
[4734545.110273] xc5000: Successfully identified at address 0x61
[4734545.110276] xc5000: Firmware has not been loaded previously
[4734545.111271] au8522 5-0047: attaching existing instance
[4734545.156545] xc5000 5-0061: attaching existing instance
[4734545.161519] xc5000: Successfully identified at address 0x61
[4734545.161523] xc5000: Firmware has not been loaded previously
[4734545.161530] DVB: registering new adapter (au0828)
[4734545.161535] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[4734545.162028] Registered device AU0828 [Hauppauge HVR950Q]
[4734740.822486] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 2)
[4734740.849449] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on TV encoder (output 2)
[4734740.849455] [drm] nouveau 0000:01:00.0: Output TV-1 is running on CRTC 1 using output B

```

---

### Post by fixitdude on 2012-06-10
In case someone finds this post via search, this thread shows you where to get the latest drivers.

[http://ubuntuforums.org/showthread.php?t=1980540](http://ubuntuforums.org/showthread.php?t=1980540)

or search for "git clone git://linuxtv.org/media_build.git"

---


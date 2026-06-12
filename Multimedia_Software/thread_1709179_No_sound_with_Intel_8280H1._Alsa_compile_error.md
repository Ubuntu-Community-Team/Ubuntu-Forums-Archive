---
title: "No sound with Intel 8280H1. Alsa compile error"
date: 2011-03-17
forum: Multimedia Software
---

### Post by SlingerXL on 2011-03-17
Hello,

I'm running 8.10 (backtrack 4), and sound suddenly stopped working. For the first few months sound was ok but every now then the sound would begin to stutter and get stuck. A reboot fixed it everytime. Now the sound is gone. I've purged alsa packages and then reinstalled then as per the sticky but that didn't work so I tried compiling the alsa driver from source and I get this error after make && make install:

```
make[3]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9474;
          &#9474; /usr/bin/make -C /usr/src/linux-headers-2.6.35.8 SUBDIRS=/usr/src/modules/ &#9474;
          &#9474; make[3]: Entering directory `/usr/src/linux-headers-2.6.35.8'              &#9474;
          &#9474; /usr/src/linux-headers-2.6.35.8/arch/x86/Makefile:39: /usr/src/linux-heade &#9474;
          &#9474; make[3]: *** No rule to make target `/usr/src/linux-headers-2.6.35.8/arch/x86/Makefile_32.cpu' 
          &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.35.8'               &#9474;
          &#9474; make[2]: *** [compile] Error 2                                             &#9474;
          &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9474;
          &#9474; make[1]: *** [build-stamp] Error 2                                         &#9474;
          &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9474;
          &#9474; make: *** [kdist_image] Error 2
```

More info:
```
root@xxx:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
root@xxx:~# lspci | grep udio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

```

Also already edited the audio: x:29 line to both include and exclude root and alsamixer is not muted.

Anyone know what I should do?

---

### Post by SlingerXL on 2011-03-20
Nobody? Anybody? Somebody?

---

### Post by lidex on 2011-03-21
Use the alsa-info-script to provide detailed information.
Run this command in a terminal (not as root):
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---


---
title: "Headphones plugged, speakers affected by unmute"
date: 2010-06-14
forum: Multimedia Software
---

### Post by kzer95 on 2010-06-14
Hello,
I have no sound when the headphones are plugged in.

---

### Post by kzer95 on 2010-06-25
> **kzer95 said:**
> Hello,
I have no sound when the headphones are plugged in.
up

---

### Post by Yellow Pasque on 2010-06-25
No sound in the headphones or no sound in the speakers? When you plug the headphones in, the speakers are supposed to mute. You may be able to disable this "jack sensing" feature in alsamixer.

---

### Post by kzer95 on 2010-06-25
> **Temüjin said:**
> No sound in the headphones or no sound in the speakers? When you plug the headphones in, the speakers are supposed to mute. You may be able to disable this "jack sensing" feature in alsamixer.

both speakers and headphones have no sound. without the headphones plugged, the speakers have sound

---

### Post by lidex on 2010-06-25
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by kzer95 on 2010-06-26
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)
```

john@jb-ubuntu:~$ uname -a
Linux jb-ubuntu 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
john@jb-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
john@jb-ubuntu:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                                   0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-22-generic 2.6.32-22.13                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.22.23                                    Backported drivers for alsa-driver snapshot.
ii  python-alsaaudio                               0.5+svn36-1ubuntu1                              Alsa bindings for Python
john@jb-ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
Codec: VIA VT1708S
john@jb-ubuntu:~$ 

```
My laptop is an asus K40IJ

---

### Post by kzer95 on 2010-06-27
up

---

### Post by lidex on 2010-06-27
This codec is a huge pain and I have yet to find any clear fixes. My suggestion at this point is to remove alsa-backports then reboot. Next go to alsa-upgrade link in my sig and do the full alsa upgrade to 1.0.23

---

### Post by kzer95 on 2010-07-04
> **lidex said:**
> This codec is a huge pain and I have yet to find any clear fixes. My suggestion at this point is to remove alsa-backports then reboot. Next go to alsa-upgrade link in my sig and do the full alsa upgrade to 1.0.23

I did the upgrade but the problem persists.

```

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.

Here is my alsa-info: http://www.alsa-project.org/db/?f=b47950359b3f33faea46dd28b0daddebc1ebcf98

```

---

### Post by lidex on 2010-07-04
Looks like the upgrade wasn't complete. Alsa-backports still installed?
What is this output:
```
dpkg -l | grep "alsa"
```

---

### Post by kzer95 on 2010-07-04
> **lidex said:**
> Looks like the upgrade wasn't complete. Alsa-backports still installed?
What is this output:
```
dpkg -l | grep "alsa"
```

```
john@jb-ubuntu:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                          1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-modules-2.6.32-22-generic                 1.0.22.1+dfsg-0ubuntu3+2.6.32-22.36             ALSA modules for kernel 2.6.32-22-generic
ii  alsa-oss                                       1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                                    1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                     1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                                 1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                                   0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
rc  linux-backports-modules-alsa-2.6.32-22-generic 2.6.32-22.13                                    Ubuntu supplied Linux modules for version 2.
ii  python-alsaaudio                               0.5+svn36-1ubuntu1                              Alsa bindings for Python

```

I see the backports there but when I tried to remove it

```
john@jb-ubuntu:~$ sudo apt-get remove linux-backports-modules-alsa-2.6.32-22-generic 
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-backports-modules-alsa-2.6.32-22-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Also, I uninstalled PulseAudio. It fixed the problem; but now I do not have volume keyboard shortcuts.

---

### Post by Yellow Pasque on 2010-07-06
> **kzer95 said:**
> Also, I uninstalled PulseAudio. It fixed the problem; but now I do not have volume keyboard shortcuts.
Use this PPA to restore volume control and media keys when not running pulse: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by kzer95 on 2010-07-09
> **Temüjin said:**
> Use this PPA to restore volume control and media keys when not running pulse: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

Thanks that worked!

---


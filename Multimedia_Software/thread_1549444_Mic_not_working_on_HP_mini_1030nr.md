---
title: "Mic not working on HP mini 1030nr"
date: 2010-08-09
forum: Multimedia Software
---

### Post by Dunpostin on 2010-08-09
I recently installed Ubuntu Netbook on my computer and everything works fine except for the internal mic. I can't make it work properly. I'm completely new to Ubuntu and I don't know how to configure settings properly. When I run sound recorder and record all I get is a rustling sound. Left some screenshots of the settings, if that helps in anyways. Will appreciate any help on this.

---

### Post by lidex on 2010-08-09
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

### Post by Dunpostin on 2010-08-10
```
Linux jovany-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
jovany@jovany-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jovany@jovany-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                              1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                             1.0.22-0ubuntu5                                 ALSA utilities
rc  alsamixergui                           0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                             4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                        0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                     0.10.28-1                                       GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa                   1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA 
jovany@jovany-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: IDT 92HD75B2X5

```

---

### Post by Dunpostin on 2010-08-10
and it's an HP Mini 1030nr

---

### Post by Dunpostin on 2010-08-10
Never mind I got it working.I just had to go into sound preference and change the connector to "Line-in/Microphone". Then I adjusted a couple of settings in Alsamixer and it worked.

---

### Post by lidex on 2010-08-11
Good deal. Would you please mark the thread solved so I'll quit clicking on it ;)
Use 'Thread Tools' up top. Thanks.

---

### Post by snjib on 2010-09-24
Hi,
I have exactly the same specification HP Mini 1030NR. I installed netbook edition of Ubuntu 10.4. Unfortunetely internal microphone does not work even after some changes in System->Preferences->Sound, etc. . And I have no idea what to do. 
May I get help step by step?:???:

---


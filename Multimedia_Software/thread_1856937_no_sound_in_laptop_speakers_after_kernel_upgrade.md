---
title: "no sound in laptop speakers after kernel upgrade"
date: 2011-10-09
forum: Multimedia Software
---

### Post by kobbi on 2011-10-09
hey guys,
Laptop compaq presario cq56 has no sound through laptop speakers after kernel upgrade. Sound works in headphone jack. This is only an issue if the computer starts up in the two newest kernels 2.6.32-33 and 2.6.32-34.

The speakers work in 2.6.32-32

here's some info from the terminal:

XX@XX-ubuntu:~$ uname -a
Linux XX-ubuntu 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:40:53 UTC 2011 i686 GNU/Linux

XX@XX-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

XX@XX-ubuntu:~$ dpkg -l | grep "alsa"
ii  alsa-base                                   1.0.22.1+dfsg-0ubuntu3                     ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                      4.60-0ubuntu8                                 Bluetooth audio support
ii  gnome-alsamixer               0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-32-generic    2.6.32-32.201107141603                          Ubuntu-supplied Linux modules for version 2.

XX@XX-ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ID 270

---

### Post by zaza1851983 on 2011-10-09
same problem here
laptop dell inspiron M4400
Ubuntu 10.04 LTS 64bits

---

### Post by kobbi on 2011-10-27
does no one have a solution, or am I posting this wrong somehow?

---

### Post by kobbi on 2011-11-20
ubuntu community my ***

---

### Post by shivathreya on 2011-11-20
Install gnome-alsamixer and ensure that all channels are unmuted and to its maximum.

That should work.

Shiva

---

### Post by gordintoronto on 2011-11-20
Have you tried running a LiveCD of Ubuntu 11.10?

---

### Post by kobbi on 2011-11-21
gnome-alsamixer installed

channels are unmuted

---

### Post by kobbi on 2011-11-21
I'm running 10.04, why would I run a LiveCD of 11.10 ?

---

### Post by gordintoronto on 2011-11-21
Because the problem you are complaining about is almost certainly solved in 11.10? I have a laptop which had sound issues, but they are ancient history for me now.

---

### Post by beew on 2011-11-21
Just boot into the old kernel and delete the new one,--along with its two headers,-- problem solved. :) Well I hope You haven't deleted the old one yet.

---


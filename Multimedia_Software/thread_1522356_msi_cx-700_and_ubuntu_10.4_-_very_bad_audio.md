---
title: "msi cx-700 and ubuntu 10.4 - very bad audio"
date: 2010-07-02
forum: Multimedia Software
---

### Post by gimzi on 2010-07-02
Hi!
I'am used msi cx-700 and ubuntu 10.4. 
The problem consists in that &#1072;udio  signal of bad quality and is very silent. Also the speaker works only on one of two loudspeaker.
Audio card - Realtek alc888 is defined.
Alsa is established.
Tried many different variants of correction of the given problem, has reconsidered a forum, has helped nothing. Otherwise would not write.
Please help!!! Forgive for bad English. =)

---

### Post by gimzi on 2010-07-06
**Excellent support!!! Many thanks! Really it is better to use a paid software though will help if that...**

---

### Post by lidex on 2010-07-07
Sarcastic much? :rolleyes:
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
Was this an update or fresh install?

---

### Post by gimzi on 2010-07-11
[FONT=Arial Black][SIZE=1]preved medved!  =))))
No, it is severe Ruessian humour =)
Excuse that long did not answer.
#
vanzai@vanzai-laptop:~$ uname -a
Linux vanzai-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
vanzai@vanzai-laptop:~$ aplay -l
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: SIS966 [HDA SIS966], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: ALC888 Analog [ALC888 Analog]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;(Under devices ?): 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086;(Under devices ?) &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 0: SIS966 [HDA SIS966], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 1: ALC888 Digital [ALC888 Digital]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;(Under devices ?): 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0(Under devices ?): subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: HDMI [HDA ATI HDMI], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 3: ATI HDMI [ATI HDMI]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;(Under devices ?): 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0(Under devices ?): subdevice #0
vanzai@vanzai-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
vanzai@vanzai-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
#
 is fresh installation

[/SIZE][/FONT]

---

### Post by lidex on 2010-07-11
What is your model number and manufacturer?

Have you checked/adjusted your levels?
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by gimzi on 2010-07-11
I'm install gnome-alsamixer, checked levels, have not helped.
model notebook :MSI X-700 (MS-1731).
model audiocard; RTL 8187SE (MS-6894).

---

### Post by lidex on 2010-07-11
OK. Upgrade your alsa install via the alsa-upgrade link in my sig.

---


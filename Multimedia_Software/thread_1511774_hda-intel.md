---
title: "hda-intel"
date: 2010-06-17
forum: Multimedia Software
---

### Post by kahnoie on 2010-06-17
hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj

uname -a
Linux amit-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
( Ubuntu 10.04 LTS- the Lucid Lynx)

---

### Post by lidex on 2010-06-17
Do you have audio?
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

### Post by mau5 on 2010-06-26
After the last update the desktop was loaded slowly. Laptop HP ProBook 4515s
dmsg
```
[ 15.671503] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```

uname -a
```
Linux mau5-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
```

aplay -l
```
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: SB [HDA ATI SB], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: AD198x Analog [AD198x Analog]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: HDMI [HDA ATI HDMI], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 3: ATI HDMI [ATI HDMI]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
```

dpkg -l | grep "alsa"
```
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                       14.3.0-1.1build1                                SoX alsa format I/O library
```

head -n 1 /proc/asound/card*/codec#*
```
==> /proc/asound/card0/codec#0 <==
Codec: Analog Devices AD1984A

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
```

---


---
title: "Acer 8942g + Ubuntu 15.04 - just 1 speaker works"
date: 2015-04-25
forum: Multimedia Software
---

### Post by Bear_Ukraine on 2015-04-25
Hi guys.

I have the next issue:
There is a laptop Acer 8942g with "5.1", but I would be happy to get at least 2.0, because for now just 1 right speaker works.
In 14.04 and 14.10 2 speakers worked (2.0 - stereo\left and right).
I tried clean instalation of 15.04 and upgrade from 14.04 to 15.04 and also tried to play with different settings of alsamixer.

Could you help me pls and tell me which info u need (logs, outputs of commands, etc.).
Thank you.

aplay -l
```
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: MID [HDA Intel MID], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: ALC669X Analog [ALC669X Analog]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 0: MID [HDA Intel MID], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 1: ALC669X Digital [ALC669X Digital]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 1: HDMI [HDA ATI HDMI], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 3: HDMI 0 [HDMI 0]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0

```

---

### Post by Bear_Ukraine on 2015-04-25
Solved

sudo gedit /etc/modprobe.d/alsa-base.conf
At the end of the file adding
options snd-hda-intel model=asus-mode1

---

### Post by Bear_Ukraine on 2015-04-25
Found additional problem caused by "options snd-hda-intel model=asus-mode1" - internal mic stoped working. Can anyone help?)
Thanks.

---


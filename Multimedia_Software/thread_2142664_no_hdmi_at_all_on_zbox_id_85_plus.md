---
title: "no hdmi at all on zbox id 85 plus"
date: 2013-05-06
forum: Multimedia Software
---

### Post by kartsims on 2013-05-06
Hello everyone,

This is my first post here so let me start by a big THANK YOU for answering questions on the forum. First time I post myself but have been there maaany times and always got plenty of useful information, you saved my life (OK not my life but certainly my time) a million times. But for the first time I couldn't find the solution of my problem... here I go :

I bought a Zotac Zbox (ID-85 plus) and a videprojector (Benq W1070, awesome!) to make myself a nice HTPC setup. Tried it and works great, except... I can't get HDMI port to work ! I wanting to install Ubuntu through HDMI, but had to use VGA to have a display :-( It hasn't worked since.

The setup :
- Zotac Zbox ID 85 plus (has intel graphics, no nvidia here)
- Ubuntu 13.04 (upgraded from 12.10 that wasn't working either, has intel proprietary drivers installed)
- Videoprojector Benq W1070

I shall also say that HDMI cable and projector are both working since I connected another laptop on it and it went just fine.

This is the result of xrandr command, has two HDMI ports (I got only one, looked suspicious to me)

```

sims@ZBOX:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1920x1080      60.0*+
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768      120.0     75.1     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```

Everytime I tried to plug it in and reboot or change projector's source I get "no HDMI signal". Do you see any options ? Or a way to test my hardware (it's brand new but you never know...) ?

---

### Post by kartsims on 2013-05-06
You might find this useful too :

```

sims@ZBOX:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

---

### Post by kartsims on 2013-05-07
anyone ?...

---

### Post by kartsims on 2013-05-15
:'(

still no idea ?...

---


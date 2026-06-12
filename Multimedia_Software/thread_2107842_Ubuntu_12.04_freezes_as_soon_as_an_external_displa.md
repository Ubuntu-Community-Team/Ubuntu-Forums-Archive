---
title: "Ubuntu 12.04 freezes as soon as an external display is connected."
date: 2013-01-22
forum: Multimedia Software
---

### Post by avdmys on 2013-01-22
Hello everyone,

I am using ubuntu 12.04 LTS on my acer laptop. Details are:
acer 5750G 
i5 second gen.
4 GB ram.
dual boot with win 7 and ubuntu.

Problem:
Ubuntu freezes completely when an external display is connected to it. keyboard, mouse or ctrl+alt+f1 nothing responds. It freezes when it is connected to projector through VGA cable or to HD TV using HDMI cable(I have tried only projector and TV as external display).

Observations:
1) if you connect the external display **before booting** and then power on, it works fine. But once the external display that is being used is removed when ubuntu is running it again freezes.

2)The ubuntu doesn't exactly freeze at the instant it is connected. It freezes after few seconds doesn't matter what you do.(most of the time it freezes immediately when clicked on the dash board icon or try and open any files like ppt).

3) I have even tried re-installing ubuntu, but no difference.


This is becoming troublesome especially at the time of presentation,etc.... I hope someone can help me out with this problem.

Thank you.

---

### Post by omeomi on 2013-01-23
Which graphics card do you have and which driver did you install?

---

### Post by avdmys on 2013-01-24
sorry for the delay in reply.

I have built in Intel graphics(2 GB i think) and a 1GB nvidia 540m graphic card. In windows 7 there is nvidia optimus which switches between the two graphic card as needed. But in any case intel graphic card is used first always. In ubuntu intel graphic is used. when in ubuntu the system is to get really heated up as nvidia card is to heat up even though it was not being used. A solution was found to turn off nvidia card in ubuntu, for details :

echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

running these turns off the nvidia card and dosent heat up now.



The nvidia card is not in use in ubuntu only intel graphics is used.

---


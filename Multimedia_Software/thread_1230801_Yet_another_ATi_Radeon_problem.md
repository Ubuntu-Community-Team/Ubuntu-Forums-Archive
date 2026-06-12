---
title: "Yet another ATi Radeon problem"
date: 2009-08-03
forum: Multimedia Software
---

### Post by todor943 on 2009-08-03
Hello! I'm sorry if I'm asking for something already in the forums. I'm using ATi Radeon 9200SE video card on Ubuntu 9.04. Currently (i think) I'm running it on the Open-Source drivers, but the graphic performance is very poor compared to that of the same machine running Windows XS SP2. I don't know if this is just the driver being slow or is it misconfigured.
Here's my xorg.conf 

```
Section "Device"
    Identifier    "Radeon 9200SE"
    Driver        "radeon"
    Option          "XAANoOffscreenPixmaps"
    Option          "AGPMode" "1"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Radeon 9200SE"
    DefaultDepth    24
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option         "Composite" "Enable"
EndSection
```Is there anything wrong or micofigured of nonoptimal here or is it just supposed to run that way? I'm getting mixed opinions for fglrx since it doesn't support 9200. Or does it?? I'm getting really confused now. What do I need to do/fix/install/edit/whateva in order to make it work to it's fullest? Please help! Thank you!

---

### Post by steefjeqv on 2009-08-04
Hi,

Try removing the two options in the section "Device".

Normally the driver is called "ati" in stead of "radeon", but this shouldn't make a performance difference (ati also loads the radeon driver).

Greetings,
Steven

---

### Post by martinbaselier on 2009-08-04
Peformance of video cards in linux is lower than under windows. It's kind of hard to write a driver if you don't get specifications from the manufacturer. 

If you check the ati site for linux drivers, you can find a driver from 2006. It won't work in current linux versions.

I'd advise you to turn off visual effects. It won't look so flashy but your system will be faster. 

What does **glxinfo | grep render** show?

and what's the output of:
**cat /var/log/Xorg.0.log | grep EE**

---

### Post by markbuntu on 2009-08-06
Well, ATI has released all the card and driver specs it can, especially for older cards like the 9200. If you are having problems with the ati or radeon driver you should look here. 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by chemamar on 2009-08-06
> **todor943 said:**
> Hello! I'm sorry if I'm asking for something already in the forums. I'm using ATi Radeon 9200SE video card on Ubuntu 9.04. Currently (i think) I'm running it on the Open-Source drivers, but the graphic performance is very poor compared to that of the same machine running Windows XS SP2. I don't know if this is just the driver being slow or is it misconfigured.
Here's my xorg.conf 

```
Section "Device"
    Identifier    "Radeon 9200SE"
    Driver        "radeon"
    Option          "XAANoOffscreenPixmaps"
    Option          "AGPMode" "1"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Radeon 9200SE"
    DefaultDepth    24
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option         "Composite" "Enable"
EndSection
```Is there anything wrong or micofigured of nonoptimal here or is it just supposed to run that way? I'm getting mixed opinions for fglrx since it doesn't support 9200. Or does it?? I'm getting really confused now. What do I need to do/fix/install/edit/whateva in order to make it work to it's fullest? Please help! Thank you!

I have ATI Radeon 9800 pro, with open source, and I can state with no doubt, that at this moment, it works better with Ubuntu 9.04 than with Windows XP (last drivers from ati for windows xp). If you want you can try my configuration:
```
Section "Device"
	Identifier	"Configured Video Device"
        Option "EnablePageFlip" "True"
	Option "MigrationHeuristic" "greedy"
	Option "AccelMethod" "EXA"
        Option "AccelDFS" "true"
	Option "RenderAccel" "on"
        Option "AGPMode" "8"
	Option "FBTexPercent" "0"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---


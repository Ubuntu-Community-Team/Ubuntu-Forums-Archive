---
title: "Ubuntu 14.04 Resolution problems"
date: 2015-06-23
forum: Multimedia Software
---

### Post by faisal4 on 2015-06-23
Hey guys i just switched from windows 7 to ubuntu 14.04 so i'm generally new to this,so i have ran into some problems , which are resolution problems , generally my resolution settings are 1920x1080 (16.9) 60htzs , its currently staying at 1024x768 (4:3).
my graphics card is nvidia gtx 750 so it should support my settings , when i used xrandr to see whats the problem it said:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  
  1920x1080 (0x1b8)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz

I have checked a couple of sites , and forums discusing this but i haven't found a solution to this problem yet .
i'm also running dual monitors and i didn't know how to activate the other monitor , i checked with the system setttings and got nothing just the main monitor, 
. any idea how to fix this ?

---

### Post by Yellow Pasque on 2015-06-26
Add this PPA and install the 352 series drivers: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---


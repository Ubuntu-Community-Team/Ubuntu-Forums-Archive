---
title: "Off center video display"
date: 2013-04-05
forum: Multimedia Software
---

### Post by NooB Frank on 2013-04-05
Hi all,

Thanks in advance for your help!
I have troubles adding a new resolution setting for my 42” lcd flat screen.  I read all the steps and add it – but it shows up about 3” off to the left.  

Dell SX280 
P4 3.2GHz
1GB RAM
Integrated video card – no expansion slots so no other option available. 

Fresh install of Xubuntu 12.042 LTS 

I set the pc up with my desk monitor and 1024x768 worked fine. 

But when I carry the pc into the tv room the big screen I’d like 1200x720.  Based on searching the forums I tried this:


```
test@test:~$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
test@test:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
test@test:~$ xrandr --addmode VGA1 1920x1080_60.00

```
Okay – so actually – the above text is from adding a 1920 x 1080 resolution.  I am really looking to add a 1280 x 720 to give the video card a little breathing room.  

When I do the same thing with substituting the 1280x720 parameters – the screen is off the left hand side of the monitor.   

I reset the tv and tried everything else I can think of. 

What should I try next?

Thanks in advance for any help!!

Frank.

---


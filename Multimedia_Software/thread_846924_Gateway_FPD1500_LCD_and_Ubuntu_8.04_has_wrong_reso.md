---
title: "Gateway FPD1500 LCD and Ubuntu 8.04 has wrong resolution"
date: 2008-07-02
forum: Multimedia Software
---

### Post by robkermit on 2008-07-02
Hello, I am having a problem with my monitor in Ubuntu Linux, and I need your help to solve the problem and get it working correctly. I just got an ATI Radeon 9250 PCI 256 MB video card and a Gateway FPD1500 LCD. The LCD will only hook up to the PC through the DVI port.

When I startx the resolution is not correct and about 1/3 of the right side of the screen is cut off. There is no resolutions shown when I go into the Screen Resolution option, and dpkg reconfigure xserver-xorg does not help.

Any assistance or suggestions you can provide would be greatly appreciated.

---

### Post by untermensch on 2008-07-02
Boot up, like normal. When your desktop comes up open a terminal and type sudo shutdown now. enter your password and x will start to shut down. it will give you four options. one of them is fix x ? or xfix, something like that. anyway, scroll down and choose it. It will fix your x and bring you back to the same page, then click start normal boot up and everything should be ok =]

Hope that helped!

---

### Post by robkermit on 2008-07-02
> **untermensch said:**
> Boot up, like normal. When your desktop comes up open a terminal and type sudo shutdown now. enter your password and x will start to shut down. it will give you four options. one of them is fix x ? or xfix, something like that. anyway, scroll down and choose it. It will fix your x and bring you back to the same page, then click start normal boot up and everything should be ok =]

Hope that helped!

Thanks for the help, but unfortunately this did not help. It still comes up in the wrong resolution, and there are no modes displayed under the Screen Resolution option. Clicking Detect Displays doesn't seem to do much either.

---

### Post by untermensch on 2008-07-02
Wow, that's really weird. I've never seen that problem =[ sorry. I'm not sure what to tell you. Are you dual booting?

---

### Post by robkermit on 2008-07-11
Sorry for the delay in replying. No, there is no dual boot in this machine. I have it set to not load gdm on startup, it boots straight to a the terminal login screen. After it starts, I run startx.

I am using Ubuntu Server Edition, and this server sits in a small closet and hopefully this problem can be solved so that I won't have to put a CRT monitor in the server closet or purchase another LCD that I will not use that often.

Anyone else have any ideas that may get this thing to work like it should?

Thanks.

---

### Post by robkermit on 2008-07-11
OK guys and girls, I have been digging deep on the Internet to come up with a working solution for this monitor. I have used a lot of the ideas in several different threads throughout the Internet and a few ideas of my own to get this monitor to work right. This page ([http://ubuntuforums.org/showthread.php?t=697420](http://ubuntuforums.org/showthread.php?t=697420)) give me a few ideas to try and I have finally got this working properly. If someone else can come up with a better way to write this then please do. I am new to Linux and if it works, it works as far as I'm concerned.

Here is the code I am using to get this LCD to display properly on my PC.

I am using Ubuntu 8.02.

Section "Monitor"
Identifier "FPD1500"
VendorName "Gateway"
ModelName "FPD1500"
HorizSync 30-61
VertRefresh 56-76
Option "IgnoreEDID" "on"
ModeLine "1024x768" 65 1024 1048 1184 1344 768 771 777 806 -vsync
EndSection 

Section "Screen"
Identifier "Screen0"
Device "Configured Device"
Monitor "FPD1500"
DefaultDepth 24
Subsection "Display"
Depth 32
Modes "1024x768" "640x480"
Virtual 1024 768
EndSubsection
Subsection "Display"
Depth 24
Modes "1024x768" "640x480" 
Virtual 1024 768
EndSubsection
Subsection "Display"
Depth 8
Modes "1024x768" "640x480"
Virtual 1024 768
EndSubsection
Subsection "Display"
Depth 16
Modes "1024x768" "640x480"
Virtual 1024 768
EndSubsection
EndSection

---


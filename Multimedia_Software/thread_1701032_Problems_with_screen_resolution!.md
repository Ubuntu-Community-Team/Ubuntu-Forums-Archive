---
title: "Problems with screen resolution!"
date: 2011-03-05
forum: Multimedia Software
---

### Post by Br1987 on 2011-03-05
Hi! I want some advice on my problem, I recently installed Ubuntu 10.04 in my computer, I ran update manager and installed all the actualizations but and I can not set the screen resolution higher than 800x600; I have windos XP installed in another partition and the screen resolution can get to 1028x1024 at 85 hz
I have a Pentium 4, 2.20 ghz, 1gb ram, and the video card is a SiS (Silicone Integrated Systems) 300/305/630/540/730 32 Mb... I don't know what can be the problem :(

---

### Post by Suikoden on 2011-03-06
I'm having the exact same problem! the highest resolution i can use is 800x600! ive tried everything i can think of to configure it! but it just doesnt seem to work! I would appreciate it if you could message me when you find a solution! thanks!

---

### Post by Br1987 on 2011-03-06
It seems that I'm not the only one... I'll let you know man, don't worry. I know there's someone out there who can help us =(

---

### Post by Br1987 on 2011-03-06
I found the solution!!
First I tried adding a new resolution with a mode line and xrandr but it did not work, I got the following message:

"The selected configuration for diplay could not be applied
could not set the configuration for CRTC 135"

So I tried editing the xorg.config file and reboot the machine and voila!! I can change the resolution to 800x600, 1024x768, and 1240x1028... 
the settings I used are this:

Section "Device"
       Identifier "Configured Video Device"
       Driver       "sis"
EndSection

Section "Monitor"
         Identifier "Configured Monitor"
         HorizSync 31.5 - 70.0
         VertRefresh 50-160
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
        DefaultDepth 24
        Subsection "Display"
             Depth 24
             Modes "1280x1024" "1024x768"
        EndSubsection
EndSection


Lucky for me another person had the same problem with the same video card! so I just copy the settings... you should find a solution for your video card!!

Now it seems that the problem is that my video card is not working properly, since everytime I play a video on Youtube, the computer crashes!!... don't know what to do... I also installed crhomium in order to see if the problem had to see with firefox or the machine, but when playinhg online videos on Youtube the computer crashes... T_T any advice here??

---

### Post by Br1987 on 2011-03-06
Confirmed, playing youtube videos completely crashes my computer... even if I'm using chromium... installed bleachbit and cleaned the firefox install but just solved the problem temporarily... =(

---


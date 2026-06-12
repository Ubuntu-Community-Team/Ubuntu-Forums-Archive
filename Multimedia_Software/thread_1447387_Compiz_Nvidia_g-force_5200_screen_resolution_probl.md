---
title: "Compiz Nvidia g-force 5200 screen resolution problem"
date: 2010-04-05
forum: Multimedia Software
---

### Post by Steve78 on 2010-04-05
Hi,
Linux Ubuntu 9.10 (karmic), Nvidia g-force 5200, Intel(R) Pentium(R) 4 CPU 2.80GHz
(old PC but i need learn Linux inside out b4 I go 100% Linux)

I am a Linux newbie. But I have taken the time to the learn the basic cmds like man mv cp apt-get install etc. I cisco engineer but I want to get good with Linux distro's
I have a NVIDIA G-FORCE 5200 which according to NVIDIA'S website the 173.14.x.x driver is the correct one
I have tried diver 173.14xx. I installed it manually and restarted x server. I have read the installation guides on this forum but to no avail.
When I reboot Compiz cube features are working BUT my screen goes 640x350.
I tried to edit the /etc/X11/xorg.conf file but I cant see any screen resolutions lines. I tried changing NV to nvidia and visa versa. Still the screen is buggered
I installed compiz checker and ran it it said all ok. My text goes large the colours are jittery ? When I go to NVIDIA XSERVER SETTINGS i can not change the screen res ? It just stops from selecting the options ?
I also tried driver 185.18xx and the same results.
I also tried installing the drivers with Envy NG and still no better.
I now have installed 96.43.13 NVIDIA driver and my screen has went back to normal but I can not enable the cube effects. I take this means it has reverted back to the graphics card on the motherboard ?
I have also looked at xrandr -s <1014x768>  cmd to manually change it and again no avail.
Any help would be much appreciated.

---

### Post by Steve78 on 2010-04-06
I have managed to get the screen res back to 1024*768 after manually putting the following (see below) in the the xorg.conf file, I found on the forum. But now when I open a terminal it is just white and it shows no text or colours ? Any thoughts please

Section "Monitor"
        Identifier      "Configured Monitor"
        DisplaySize     328 248
        HorizSync       30-85
        VertRefresh     50-120
EndSection




Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

---

### Post by mörgæs on 2010-04-07
I have a Dell with the same graphics card, and everything works well in Ubuntu 8.10 running two screens. I do not use Compiz, though. 

When I get home I can take a look at the graphics drivers and tell you which ones I use. Meanwhile you could perhaps try a live boot with Ubuntu 10.04. It is in beta, but very stable on all machines I have tried it.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Steve78 on 2010-04-07
Thanks for the advice. I will try out Ubuntu 10.4 and see what happens.

---


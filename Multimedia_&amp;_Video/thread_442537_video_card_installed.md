---
title: "video card installed?"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by krisfrajer on 2007-05-13
Hi folks
How do I know my video card + drivers are installed correctly? I have an ati radeon 9600TX on an AMD64. When I try to enable desktop effects, it does not work (system cannot enable it) plus the acceleration driver when activated gives me black screen and removes ubuntu graphical interface completey ... ie when I restart my  baby  I just get this black screen. I have the feeling my card is not installed correctly. Thus:

1) is there any way to know I have the proper driver set up?
2) How can I set up my proper driver for this card?

This is what I get in my xorg.cong file @ /etc/X11
Something I want to remark is that I have a dual monitor system. i am not into configuring this system yet. I want to figure out  my card system first. i just installed ubuntu and working my way around to install the right drivers for my hardware (Yeah I also need to configure my soundblaster X-fi).

Thxs,


Section "Device"
        Identifier      "ATI Technologies Inc RV350 AR [Radeon 9600]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "F9AH(ANA)"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 AR [Radeon 9600]"
        Monitor         "F9AH(ANA)"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

---

### Post by cgizmo on 2007-05-14
If you have Ubuntu Feisty, go to System -> Administration -> Restricted Drivers Manager, then check the driver corresponding to your video card.
By the way, the desktop effects didn't work for me either, I had to install XGL and Beryl.

Hope I helped you:lolflag: !

---

### Post by krisfrajer on 2007-05-15
ATI accelerated graphics driver... that is what I get in that settings >> restricted drivers menu. I was expecting something related to my graphic card ATI radeon 9600XT. Choosing that option just drives my screen into an infinite black dark quite screen. I have to reboot my computer and restore the xorg.confg file manually. I am assuming at this point that my drivers are not correctly installed and I am having so much trouble with this architecture AMD64. The set up is not straight forward but I have not given up in the installation.... yet.

What is that XGL that you mention in the last post? Should I installed it before Beryl?

---


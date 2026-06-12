---
title: "Poulsbo driver installation on 9.10 ?"
date: 2010-11-30
forum: Multimedia Software
---

### Post by am577 on 2010-11-30
The Poulsbo support page here:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
suggests that Poulsbo support is broken in 10.10 but 'Excellent' in 9.10. 
When I installed the driver in 10.10 it installed OK, and works OK except for video playback.
When I then tried to install it on 9.10 using the same procedure, it downloaded the drivers but then did not automatically build/install/configure them, and there was no change to the video behaviour. I presume it simply didn't execute the relevant scripts etc after downloading the packages.
What might have gone wrong ? What else can I try ? The terminal command I used in both cases was similar to this:
sudo add-apt-repository ppa:gma500/ppa && sudo apt-get update && 
sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-configThe system is a Dell Mini 12, which uses the Intel GMA500 Poulsbo chipset.
AM

---

### Post by fjgaude on 2010-11-30
I'm dealing with similar issues with the Poulsbo chipset in a Dell mini 10n with 1366 x 768 screen resolution. Will let you know if I get it working better with these drivers. I'm using either OS 10.10 or 10.04.

An hour or so has past!

Okay, I ran the script and it worked perfectly on ubuntu 10.10 installed on my mini 10n and auto-detected the 1366 screen. Wow! am I happy! I will try next with a 10.04 install. Never liked 9.10 thou 9.04 is fine. So I'll not try either of these on the mini.

---

### Post by m0dcm on 2010-12-01
I had that problem on my Acer Aspire One AO751h when I re-installed back to 9.10 the other week, till I noticed that  after installing the drivers it didn't update the Xorg.conf file, so I  did it myself.
Do a sudo gedit /etc/X11/xorg.conf and add the following (This is for 9.10!!)....

Section "Device"
        Identifier      "GMA500"
        Driver         "psb"
        Option          "DRI" "on"
        Option         "IgnoreACPI" "true"

        Option         "MigrationHeuristic" "greedy"
        Option         "DownScale" "false"
    Option          "AccelMethod" "UXA"
        Option         "ExaNoComposite" "false"
    Option        "ExaScratch" "4"
    Option        "ExaCached" "false"
        Option         "LidTimer" "false"
        Option         "NoAccel" "false"
        Option        "NoFitting" "false"
        Option         "NoPanel" "false"
        Option         "ShadowFB" "false"
        Option         "SWcursor" "false"
        Option         "Vsync" "false"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
    Option        "RENDER" "Enable"
EndSection

This will get the resolution and the items working for you, hope this helps???

---

### Post by fjgaude on 2010-12-01
Great! on the 9.10. My 10.10 works fine as there really is no xorg.conf with it. But I've not gotten the mini to come out of suspend... it is said it can. I see the code offered but it doesn't work, yet. Will try other things suggested.

---


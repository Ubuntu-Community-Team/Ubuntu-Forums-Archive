---
title: "Nvidia Video and Audio setup nightmare!"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by syn-rg on 2008-02-09
ok so Ive decided to get up and try Linux again after a 10 year absence!  I used to Run slackware and X when I was in college and loved it.  I thought it was about time to give it another try with Ubuntu.

So anyway, this whole configuring process with Ubuntu is a nightmare.  Nothing seems to work properly and I never had so many problems with Linux.  Im just about to head back to winblows and say screw it.   

Ive installed the Nvidia drivers, get them working, got the dual displays working and then when I reboot everything goes back to low res mode and its not using the Nvidia driver anymore!! grrr!!!  I have to re-install the driver to get it to work!  I have NO CLUE why this is happening.

Also,  I have a Realtec ALC883 onboard HD sound and a M-Audio Delta 44 soundcard in my computer.  They all seem detected under the Sound Settings but there is NO SOUND! ARG!  So anyway I installed OSS-Linux and guess what?!?! I had SOUND!! THen I rebooted and and LOW AND BEHOLD my video drivers went back to low res AND THE SOUND was not working anymore! Oh nice.  Now Im trying to remove the OSS-Linux package and oh yes it wont let me do that, gives me all sorts of error at the console when I try to remove as root with no X running.  

This all seems fairly ridiculous to fight for every step here.  Ive done some searching around but it seems there are SO MANY unique problems that nothing is right for so many issues!  

Can anyone offer some help to understand why my Nvidia drivers seem to work fine and then unload themselves after rebooting?  Also what the hell is going on with my sound?!?   Its all detected but there is no sound!  I am running Optical from my Realtec card to an amp and I am running 1/4" from my Maudio Delta to the Monitors!

Help

---

### Post by syn-rg on 2008-02-09
These are the errors I get when I try to uninstall OSS-Linux.

root@syngen:/home/synergy/Desktop# sudo dpkg --purge oss-linux
(Reading database ... 91500 files and directories currently installed.)
Removing oss-linux ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux (--purge):
 subprocess pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux

---

### Post by syn-rg on 2008-02-09
These are the errors I get when I try to re-install OSS-Linux.  Just so you know I originally installed OSS-Linux from X as the installer had a gui.

root@syngen:/home/synergy/Desktop# sudo dpkg --purge oss-linux
(Reading database ... 91500 files and directories currently installed.)
Removing oss-linux ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux (--purge):
 subprocess pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux

---

### Post by syn-rg on 2008-02-09
Here is my xorg.conf.  As I said before, I install the Nvidia driver at the console.  Everything works fine.   I start X and its beautiful.  Whenever I reboot the driver doesnt load again and Im back at low res with a basic driver.  


Section "Monitor"
    Identifier     "NEC FE950+"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC FE950+"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SHARP HDMI"
    HorizSync       15.0 - 68.0
    VertRefresh     55.0 - 76.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "NEC FE950+"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024_85 +0+0; CRT: 1280x1024 +0+0; CRT: 1280x960 +0+0; CRT: 1152x864 +0+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 720x400 +0+0; CRT: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1280x768_60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

---


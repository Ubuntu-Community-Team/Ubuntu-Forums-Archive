---
title: "Catalyst Control Center not saving changes"
date: 2010-03-15
forum: Multimedia Software
---

### Post by iwtws on 2010-03-15
Catalyst Control Center (CCC) is not saving the changes I make. I saw a couple of thread about this that had links to instructions on how to install CCC, but it still doesn't work for me.

Any suggestions welcome.

I start CCC with 'sudo amdcccle' and the GUI appears. I can use it to make changes; however, it never saves them. After clicking OK, it instructs me to restart the system. After a reboot all the setting are back to the default.

I have installed CCC three different ways:
1) sudo aptitude install --without-recommends fglrx-amdcccle | tee fglrx-amdcccle.log
2) sudo envyng -t
3) sudo ./ati-driver-installer-10-2-x86.x86_64.run

In all cases, the fglrx driver works, and 'sudo amdcccle' brings up the GUI, but the changes are gone after a reboot.

Hmm, at the moment, when I click "Apply" and the "Do you want to keep these settings?" 15 second countdown box appears, no changes occur even temporarily.

I've tried doing a fresh install of 9.04, then upgraded to 9.10 (I have problems with the 9.10 command line installer not installing grub) among other things.

---

### Post by iwtws on 2010-03-16
I now have it working, with four monitors on four outputs, two each on two different ati video cards (one is is built in to the motherboard).

I did it from a fresh install, but I think this would have fixed my catalyst problem:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.<insert_something_here>
sudo mv /etc/ati/amdpcsdb /etc/ati/amdpcsdb.<insert_something_here>

amdcccle will create a new amdpcsdb, but I needed an xorg.conf to even start X to be able to run amdcccle:

```
Section "ServerLayout"
    Identifier     "Basic fglrx"
    Screen      0  "Screen1" 0 0
    Screen      1  "Screen0" RightOf "Screen1"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Device"
    Identifier  "Device0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "Device1"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Device0"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Device1"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection


```My steps went something like this:

[LIST=1]
[*]Install a command line 9.04
[*]upgrade to 9.10
[*]install xorg menu openbox leafpad build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms libQtGui4 linux-headers-$(uname -r)  libelfg0 execstack
[*]# ./ati-driver-installer-10-2-x86.x86_64.run --buildpkg Ubuntu/karmic
[*]# dpkg-i *.deb
[*]create /etc/X11/xorg.conf with contents as above
[*]$ startx
[*]# amdcccle
[/LIST]
If you did a normal install (not a command line only one), you won't need to install xorg, menu, openbox, or leafpad, but the other packages are necessary for building the .debs

---


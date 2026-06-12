---
title: "xorg.conf help"
date: 2009-04-12
forum: Multimedia Software
---

### Post by vajeen on 2009-04-12
my xorg.conf dosent show my vga card.vga seems to work properly but it shows as it's a defalt device.what can i do

---

### Post by markbuntu on 2009-04-12
What do you want to do?

---

### Post by vajeen on 2009-04-12
i want to adjust the login window resolution by editing the  xorog.conf

---

### Post by acimmarusti on 2009-04-12
From the 8.10 Release notes:

> X.Org Input Devices

The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from /etc/default/console-setup; to change them please use sudo dpkg-reconfigure console-setup. After that, HAL and X need to be restarted (e.g., by rebooting your system). 

I hope you know what you are doing!

---

### Post by vajeen on 2009-04-12
there should be given resolutions in xorg.conf to adjust the login winddow resolution..but in my case every thing is in defalt.so i cannot any unwanted resolution..

here's my xrog.conf
_____________________________________________________________________________
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
_____________________________________________________________________________
any ideas????

---


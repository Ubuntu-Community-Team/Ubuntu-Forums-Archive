---
title: "changed video card now no login"
date: 2008-08-20
forum: Multimedia Software
---

### Post by luusac on 2008-08-20
Hi,
I have replaced an ATI 3D Rage II PCI video card with an ATI agp radeon card (radion 2600 I think) - both are old cards.  Am running ubuntu 8.x Anyway, I can't get the login menu.  I have searched the forums and tried ctrl+alt+F1, logging in as root and entering dpkg-reconfigure -phigh xserver-xorg, I get a message about a backup being taken, other than that nothing.  Reboot doesn't bring the graphical login menu back.  I have also tried choosing recovery mode from grub and then choosing the options for dpkg and xserver repair (I forget their exact titles) and trying dpkg-reconfigure -phigh xserver-xorg again, and then reboot.  No joy.  Can anybody help please?
lu

---

### Post by KindredCharles on 2008-08-20
Try editing your xorg.conf manually?

---

### Post by luusac on 2008-08-20
to change what to what?  Sorry, but my linux/ubuntu knowledge is at a basic level ...
lu

---

### Post by KindredCharles on 2008-08-20
make a backup of it

cd /etc/X11/

sudo cp xorg.conf xorg.conf.bak

edit out the driver part and it wont try to use the old ati driver it should run in low graphics mode and let you configure from there, or you can change it to vesa.

Section "Device"
        Identifier        "Configured Video Device"
        Driver            "**vesa**"
EndSection

yours might be different you can post your xorg.conf here if this doesn't work for you.

---

### Post by luusac on 2008-08-20
> **KindredCharles said:**
> Section "Device"
        Identifier        "Configured Video Device"
        Driver            "**vesa**"
EndSection

The relevant config section was only  
Section "Device"
        Identifier        "Configured Video Device"
EndSection

adding Driver "vesa" solved the problem, on boot I am getting 1280x1024.

many thanks.
lu

---


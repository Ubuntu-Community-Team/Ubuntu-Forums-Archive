---
title: "[SOLVED] Installing Broadcom firmware"
date: 2008-08-25
forum: Mythbuntu
---

### Post by dmdbdd on 2008-08-25
OK I have finally been able to down load this firmware and it appears to be in this dir - '/b43-fwcutter-011$'. Now I tried to follow the install directions on this link [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43), however everything I try gives me error messages:(

Does anyone have a step by step procedure to get this firmware installed? Please no linux geek speak - I'm new to linux and maybe that's why I'm having trouble deciphering the above link. For example this line of code:

```
sudo ./bcm43xx-fwcutter-006/bcm43xx-fwcutter -w "$FIRMWARE_INSTALL_DIR"
```makes on sense to me and gives me an error message. It is accompanied by the following:

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your
distribution. The standard place where firmware is installed to is
/lib/firmware. However some distributions put firmware in a different
place.

OK, where does Mythbuntu store firmware and do I need to execute this code.  If I do how should this code look  when adjusted for the correct path?

---

### Post by superm1 on 2008-08-25
> **dmdbdd said:**
> OK I have finally been able to down load this firmware and it appears to be in this dir - '/b43-fwcutter-011$'. Now I tried to follow the install directions on this link [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43), however everything I try gives me error messages:(

Does anyone have a step by step procedure to get this firmware installed? Please no linux geek speak - I'm new to linux and maybe that's why I'm having trouble deciphering the above link. For example this line of code:

```
sudo ./bcm43xx-fwcutter-006/bcm43xx-fwcutter -w "$FIRMWARE_INSTALL_DIR"
```makes on sense to me and gives me an error message. It is accompanied by the following:

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your
distribution. The standard place where firmware is installed to is
/lib/firmware. However some distributions put firmware in a different
place.

OK, where does Mythbuntu store firmware and do I need to execute this code.  If I do how should this code look  when adjusted for the correct path?
On Ubuntu & Mythbuntu, just use the restricted drivers manager.  Don't bother doing it by hand

---

### Post by dmdbdd on 2008-08-26
OK, so I tried using the 'restricted drivers manager' and it shows the Broadcom B43 wireless driver 'Enabled' box is unchecked and Status is 'In use'. So I checked the Enable box and it pops up a dialog box with 'Enable' and 'Cancel' buttons. I click the 'Enable' button and I'm back to the Hardware Drives screen with the 'Enabled' box still unchecked and Status is "needs computer restart'

After I restart I get the exact same thing in the 'restricted drivers manager'. So I'm just going around in circles here! I tried disabling Networking and that doesn't help.

I appears that you can't enable this driver as long as the system thinks that this card is in use - so how do I make the system think that it isn't in use?

Regards,

dmdbdd

---

### Post by dmdbdd on 2008-08-26
OK, I figured this out :) I had to go to the Synaptic Package Manager to install this firmware.

Regards,

dmdbdd

---


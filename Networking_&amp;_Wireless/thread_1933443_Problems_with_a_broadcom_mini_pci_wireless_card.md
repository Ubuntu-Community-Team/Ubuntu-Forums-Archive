---
title: "Problems with a broadcom mini pci wireless card"
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by HeyLynx on 2012-02-29
Hello,

I have added a broadcom wireless but am having issues with its install and working.  Firstly I searched and came up with a few solutions but none have worked.

When I type lspci -vnn | grep 14e4 I get this:
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

Installing the card in the network icon, the card needed a firmware upgrade. I having tried to downloaded the b43 and b43 legacy drivers at the command prompt but kept asking me to use the installer CD.  Then I decided that this was a good time to upgrade to 11.10 of ubuntu.  Then on the restart the wireless card is no longer seen in the network icon.

Have tried installing and re-installing both the b43 and b43 legacy drivers, each one at a time and then removing the drivers.  This has been with the package manager.  Now its still not seen so don't know what to do next.

Hope someone can help.

Thanks

---

### Post by TBABill on 2012-02-29
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Then ```
sudo modprobe b43
``` If it activates with the modprobe command, then to make it permanent you can ```
gksudo gedit /etc/modules
``` and add "b43" without quotes to the end of the list and save.

---

### Post by HeyLynx on 2012-03-04
Hello


Thank you for your help, currently the last command ```
gksudo gedit /etc/modules
```brings up



```
Gtk-Message: Failed to load module "canberra-gtk-module"
```

But a wireless icon has appeared in the bottom corner saying restricted drivers with a little padlock and wireless is now greyed out on the network devices.

---

### Post by HeyLynx on 2012-03-07
Hello

Wonder if any one has an idea...

Thanks

---

### Post by TBABill on 2012-03-07
Is leafpad the text editor in LXDE? I forgot you were in Lubuntu and not Ubuntu. If so, replace gedit with leafpad and try again.

---

### Post by HeyLynx on 2012-03-08
Do I add another line or just add it to the line?

Am a total newbie at this.

---

### Post by HeyLynx on 2012-03-12
Anyone?

---

### Post by kurt18947 on 2012-03-12
> **HeyLynx said:**
> Anyone?

This may do it.  You don't need to open a text editor, just a terminal.


sudo su 
echo b43 >> /etc/modules 
exit

---

### Post by HeyLynx on 2012-03-12
Ah that worked now it says that the hardware is switched off, no matter where the switch is positioned.


Now I'm getting annoyed with this laptop. So switch is there and moves from one side to another....no idea if it works  grrrrrr

---


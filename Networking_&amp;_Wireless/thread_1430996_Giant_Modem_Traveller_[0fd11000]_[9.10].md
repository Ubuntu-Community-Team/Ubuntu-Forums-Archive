---
title: "Giant Modem Traveller [0fd1:1000] [9.10]"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by balgaltz on 2010-03-16
Ok guys, I have been googling for hours, trying and trying different "solutions" yet none seem to work, so here I am.

```

$ lsusb
Bus 006 Device 002: ID 0fd1:1000 Giant Electronics Ltd.

```
USB Modem that has only been detected as usb storage so far.

What I have tried so far:
[http://ubuntuforum-pt.org/index.php?topic=59889.15](http://ubuntuforum-pt.org/index.php?topic=59889.15)

```

1. sudo gedit /etc/udev/rules.d/10-claro3g.rules
# /etc/udev/rules.d/10-claro3g.rules
#
# Claro 3G custom rules
ACTION!="add", GOTO="3G_End"
BUS=="usb", SYSFS{idProduct}=="1000", SYSFS{idVendor}=="0fd1", PROGRAM="/
bin/sh -c 'echo 3 > /sys/%p/device/bConfigurationValue'"
LABEL="3G_End"
2. Reboot
3. Connect usb modem
4. Recognized only as usb storage.

```

---

### Post by pdc on 2010-03-16
when you plug the modem in, 

does an icon for it appear on your desktop?

---

### Post by balgaltz on 2010-03-16
No, nothing, maybe just the storage icon cuz i have disk-mounter in the panel.

---

### Post by pdc on 2010-03-16
I follow the Ubuntu forum but find a distro such as Mandriva more friendly for usb modems; how attached are you to Ubuntu? If you have access to a wired internet, try downloading the gnome version of mandriva 2010 or the latest opensuse 11.2 and try as a live CD as they configure up well ........ ubuntu 9.10 has had a tortured existence with mobile broadband ...........

---

### Post by balgaltz on 2010-03-16
Im gonna give it a try for Mandriva, but I could say that Im attached to Ubuntu.

---

### Post by balgaltz on 2010-03-16
Bump. Tried with both with no success :S

---

### Post by balgaltz on 2010-03-16
Last Bump to inform:
```
sudo gedit /etc/udev/rules.d/10-claro3g.rules
```

```
# /etc/udev/rules.d/10-claro3g.rules
# site base do script:http://www.richieri.com/2008/08/27/internet-claro-3g-no-ubuntu-804-e-satux-com-modem-giant-traveller-d301/
#
# Claro 3G custom rules
ACTION!="add", GOTO="3G_End"
BUS=="usb", SYSFS{idProduct}=="1000", SYSFS{idVendor}=="0fd1", PROGRAM="/bin/sh -c 'echo 3 > /sys/%p/device/bConfigurationValue'"
LABEL="3G_End"
```

```
sudo udevadm control --reload-rules
```

Did this on 9.04 Jaunty Jackalope 32bits LIVECD and it worked out.
Proceeding to downgrade. 

I would really like to know how this broke in Karmic.

---

### Post by pdc on 2010-03-16
well done; enjoy;

tell us what happened when you plugged the modem in

---

### Post by balgaltz on 2010-03-16
A window to config mobile broadband the one from networkmanager.

---

### Post by balgaltz on 2010-05-01
Time to continue this thread along with the new Ubuntu 10.04 Lucid Lynx.

```

#/etc/udev/rules.d/80-mobile3g.rules
ACTION!="add", GOTO="3G_End" 
SUBSYSTEMS=="usb", ATTRS{idProduct}=="1000", ATTRS{idVendor}=="0fd1", RUN+="/bin/sh -c 'echo 3 > /sys/%p/bConfigurationValue'"
LABEL="3G_End"

```

This also works for Karmic. Thread Solved

---


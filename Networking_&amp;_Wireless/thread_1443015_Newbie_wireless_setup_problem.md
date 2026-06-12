---
title: "Newbie wireless setup problem"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by RedLenin on 2010-03-30
Ubuntu 9.10
Belkin USB wireless adapter F5D8053 - this is not being detected by Ubuntu.

I have been to [https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053](https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053) for help and am trying to follow its advice. I have downloaded the Belkin driver OK (to a Windows system) but can't install Wine because apparently it's not included in Ubuntu 9.10 (according to [http://www.pendrivelinux.com/installing-wine-on-ubuntu-9-10/](http://www.pendrivelinux.com/installing-wine-on-ubuntu-9-10/) ) and I can't download the Wine package to my Ubuntu system because I obviously have no internet access yet!

Where do I go from here, please?

---

### Post by chili555 on 2010-03-30
From the link you gave us:> $ sudo ndiswrapper -i [COLOR="Red"]rt2870[/COLOR].inf 2870? Did someone say *2870*?? We have a 2870 driver native in Ubuntu, it's called rt2870sta. Let's see if your card is actually compatible. Please insert the device, open a terminal and do:```
lsusb
```Post the result and we will try to get you going quickly.

---

### Post by RedLenin on 2010-03-30
Bus 001 Device 004: ID 050d:815c Belkin Components

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Thank you!

---

### Post by chili555 on 2010-03-30
This might be your lucky day. rt2870sta does indeed support your device; however, rt2800usb does also. They often fight for wireless domination and refuse to work correctly. Let's throw rt2800usb out of school for fighting. We'll add him to the blacklist. Remove the device and open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will open. Add a new line:```
blacklist rt2800usb
```Proofread carefully, save and close gedit. Now do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Now reboot and insert the device. Is your wireless working now?

---

### Post by RedLenin on 2010-03-30
Well, the device is flashing periodically in a very healthy way (which is much more than it did before) but the icon at the top of the screen is still reporting "No network connection".

---

### Post by RedLenin on 2010-03-30
It helps if I actually click on the icon! Now it's showing my router as available and asking for a password - looks like I (or rather you!) have cracked it!

Many thanks!

---

### Post by chili555 on 2010-03-30
I was happy to help; the searchers will be happy, too.

---


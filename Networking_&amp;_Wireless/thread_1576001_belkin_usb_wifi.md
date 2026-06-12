---
title: "belkin usb wifi"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by tdm333 on 2010-09-16
hello im completly new to lunix and i cant seam to find out how to get my card to work i cant find out how to install the driver or finding the wifi card on the system can anyone help me plz and thank you

---

### Post by chili555 on 2010-09-16
The first step is to open Applications > Accessories > Terminal and ask the computer to list the USB devices:```
lsusb
```You can strip off everything that isn't a Belkin wireless device, post it here and we'll help you find and install a driver.

Welcome to Ubuntu Linux!

---

### Post by tdm333 on 2010-09-16
> **chili555 said:**
> The first step is to open Applications > Accessories > Terminal and ask the computer to list the USB devices:```
lsusb
```You can strip off everything that isn't a Belkin wireless device, post it here and we'll help you find and install a driver.

Welcome to Ubuntu Linux!



when i run terminal this is what come up owner@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 002: ID 050d:935b Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
owner@ubuntu:~$ 


i just have no idea how to install the driver for it because my driver i got for it are windows and idk where to find lunix drivers at for this wireless card btw ty for ur help

---

### Post by chili555 on 2010-09-16
We are going to try to coax a driver already in your system to drive your device. We will create two new files using the text editor 'gedit.' Please remove the device and open the terminal and do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "050d 935b" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread very carefully, save and close gedit. Now do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="935b", RUN+="/sbin/modprobe -qba rt2870sta"
```Proofread very carefully, save and close gedit.

Now plug the device back in and click the Network Manager icon and see if you can connect.

---

### Post by tdm333 on 2010-09-16
ty for your help that worked now im able to used my wifi :)

---

### Post by chili555 on 2010-09-16
Glad it's working for you! The usb.id of 050d:935b is relatively unknown, so you will have helped the searchers, too. Have fun!

---

### Post by tdm333 on 2010-09-16
> **chili555 said:**
> Glad it's working for you! The usb.id of 050d:935b is relatively unknown, so you will have helped the searchers, too. Have fun!


ty i will oh btw after you put all the code in it will not work till you do a reboot mine keep saying device not ready so i had to all the ssid manual but thank you so much for you help

---

### Post by chili555 on 2010-09-16
> it will not work till you do a rebootThank you. The searchers and I appreciate your help.

---

### Post by bayvista on 2011-03-24
I am having the same problem with a Belkin F5D7050A. I followed your instructions but without success. My lsusb is below:

Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 002 Device 007: ID 185b:0202 Compro 
Bus 002 Device 006: ID 04f9:0204 Brother Industries, Ltd 
Bus 002 Device 004: ID 064e:a110 Suyin Corp. HP Webcam
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
I changed the device to '705a'. Perhaps I need a different driver?

---

### Post by bkratz on 2011-03-24
This device ID ( 050d:705a ) seems to be in this thread

[http://ubuntuforums.org/showthread.php?t=1634022](http://ubuntuforums.org/showthread.php?t=1634022)

---


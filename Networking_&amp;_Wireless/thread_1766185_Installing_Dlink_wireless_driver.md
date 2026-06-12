---
title: "Installing Dlink wireless driver"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by seyedsharp on 2011-05-24
Everlasting...

How can I Install DLink wireless driver on Ubuntu ? 

I had downloaded the driver . The file contains some files like **MakeFile **and **ifcfg-wlan0** ,etc
+ a** tar.gz** file . which contains c or c++ source codes.

There are 4 folders also .

I am a newbie . please help

thanks in advance
regards.

---

### Post by chili555 on 2011-05-24
Before we go too crazy, let's be sure you have the correct driver for your device. Please open a terminal (Applications > Accessories > Terminal) and run and post:```
lsusb
```Feel free to trim away everything that's clearly not wireless.

What is the name of the file you downloaded?

In anticipation of compiling, can you temporarily get an ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by seyedsharp on 2011-05-24
> **chili555 said:**
> Before we go too crazy, let's be sure you have the correct driver for your device. Please open a terminal (Applications > Accessories > Terminal) and run and post:```
lsusb
```Feel free to trim away everything that's clearly not wireless.

What is the name of the file you downloaded?

In anticipation of compiling, can you temporarily get an ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```

Hi here is my lsusb result :

```
Bus 001 Device 009: ID 07d1:3c0d D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

When I put the usb wireless in , a black window + wireless signals show on the right of screen . what is that ?

---

### Post by chili555 on 2011-05-24
> When I put the usb wireless in , a black window + wireless signals show on the right of screen . what is that ?That is the Network Manager icon. It is showing that your wireless driver is installed and working and it sees networks, hopefully yours. Can you click the icon, drop down a list of networks and click yours and connect? Please see an example attached. In the example, my network is GBR1. The little yellow padlock indicates that there is encryption on the network. When I click on GBR1, I am asked for the WPA/WPA2 password. I fill it in the box and I am connected.

There is a driver conflict for your card. Please run and post:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by seyedsharp on 2011-05-24
> **chili555 said:**
> That is the Network Manager icon. It is showing that your wireless driver is installed and working and it sees networks, hopefully yours. Can you click the icon, drop down a list of networks and click yours and connect? Please see an example attached. In the example, my network is GBR1. The little yellow padlock indicates that there is encryption on the network. When I click on GBR1, I am asked for the WPA/WPA2 password. I fill it in the box and I am connected.

There is a driver conflict for your card. Please run and post:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \.


Hi I have attached my wireless network manager picture . when I connect my usb; a Wireless Option will be add .

and here is the reuslt of*** lsmod | grep rt2***

```
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb
```

---

### Post by chili555 on 2011-05-24
Please post:```
modinfo rt2870sta | grep 3C0D
uname -r
```That's a zero in there, not an O.> when I connect my usb; a Wireless Option will be add .What changes? What else shows up?

---

### Post by seyedsharp on 2011-05-24
> **chili555 said:**
> Please post:```
modinfo rt2870sta | grep 3C0D
uname -r
```That's a zero in there, not an O.What changes? What else shows up?

** modinfo rt2870sta | grep 3C0D** gives me nothing..

But **uname -r **gives me something like this :

```
2.6.31-14-generic
```

When the usb wireless device is not plugged in , there is just a wired connection , but when I connect it a wireless option will add , and there is  a disconnected button which is disabled under it.

---

### Post by chili555 on 2011-05-24
> 2.6.31-14-genericOhh! That's an oldie, but a goodie. Let's change one file and write two new files and see if we can drive your device better. Please remove the device. Open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist
```Add three lines at the end:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Now do:
```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```

Add one long line:
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c0d", RUN+="/sbin/modprobe -qba rt2870sta"

```
Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.
```
sudo gedit /etc/modprobe.d/network_drivers.conf

```
Add one long single line:
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:
```
sudo modprobe rt2870sta
```

---


---
title: "Use Droid Incredible for Mobile Broadband on Ubuntu 10.10"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by nimiaj on 2010-12-06
I recently installed Ubuntu 10.10. I wanted to setup my droid incredible as a modem to connect via the builtin broadband connection under network manager. I searched around and found couple of ways using wvdial as well as a tunneling app. The funny thing is, that I was able to setup my phone as a usbserial device and use it ONCE to connect successfully via the built-in broadband connection setup method. But ever since, it has not worked :-(. 

Currently I am running a fresh install of 10.10, and have tried to insert usbserial module for my phone in the kernel, but it does not work. The command I used :

```
sudo modprobe usbserial vendor=0x00b4 product=0x0ffb
```I have not made this change permanent though. But whenever I run this and connect my phone with broadband connect enabled, it recognizes my phone however it uses a 'generic' driver according to the logs, and it never lets me enable Broadband Connection or connect successfully.

Any help appreciated!

---

### Post by alexfish on 2010-12-06
can you remember the " /dev/ttyXXX " from wvdial , it may indicate the
which drivers to load
if these don't work try post the the tty
 
ttyUSB
For GSM :Check to see if the option drivers will load for the device:

Code:

[COLOR=Blue]sudo modprobe option[/COLOR]

ttyACM
For CDMA :Check to see if the ACM drivers will load for the device:

Code:

[COLOR=Blue]sudo modprobe cdc-acm[/COLOR]

if you make a start up script use "gksu"  not sudo

on a offchance , at some stage the device works without modprobing

run this command

Code:

[COLOR=Blue]usb_devices[/COLOR]

make a note of your device / and the driver

---


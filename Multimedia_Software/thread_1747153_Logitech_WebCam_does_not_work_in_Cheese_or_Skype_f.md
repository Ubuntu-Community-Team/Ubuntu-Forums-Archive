---
title: "Logitech WebCam does not work in Cheese or Skype for Ubuntu 11.04"
date: 2011-05-02
forum: Multimedia Software
---

### Post by Stagleton on 2011-05-02
Hey I was trying to get my WebCam to work in Skype and after looking at a few posts I decided to install Cheese because that seemed to be working for everyone, but it does not work for me. Any thoughts on what I should do?

Any help is appreciated!
thanks

---

### Post by no2498 on 2011-05-02
open a terminal type dmesg click enter

after it stops type lsusb click enter
that gives you the number and name of the cam in case you need to find a driver

in the terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

### Post by Stagleton on 2011-05-03
sweet, the camera works!..how do I get it to work with skype now?

---

### Post by no2498 on 2011-05-03
sorry im not good with skype
glad it started working tho

---

### Post by Stagleton on 2011-05-03
ok, cool. thanks for the help!

---

### Post by FaGaBa on 2011-06-22
I have exactly the same problem. I have followed the steps outlined by no248 but I got an error message when trying to test the webcam in gstreamer-properties. It says: "unable to identify /dev/video0". All was working fine before the upgrade to 11.04. Anyone has an idea how to fix this?

---

### Post by no2498 on 2011-06-22
what did lsusb say did it find the cam

you may install guvcview and xawtv 
try the cam in them

---

### Post by FaGaBa on 2011-07-13
Sorry for the delay, I was away on holidays.

lsusb says the following:

Bus 004 Device 004: ID 413c:8162 Dell Computer Corp. 
Bus 004 Device 003: ID 413c:8161 Dell Computer Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It does not seem to me that it has find the webcam, am I right?

---

### Post by no2498 on 2011-07-14
i know xawtv loads a cam grabber

you may install guvcview and xawtv 
 try the cam in them

---


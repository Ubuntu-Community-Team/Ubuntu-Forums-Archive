---
title: "Hello-totally new here and a windows convert"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by polishrose on 2011-02-10
Ok I've only been using ubuntu for 3 weeks and am liking it so far.I have come across a few things I can't work out though.This is one of them. I am going into hospital soon for an operation and would like to take my laptop with me and use mobile broadband. I have a t-mobile usb 120 stick which I would like to use but I have lost the installation cd and have no idea how to get it working on ubuntu. Does anyone here know?Step by step instructions please as I've not really had to do anything on ubuntu other than install a few browsers and skype :)

---

### Post by grahammechanical on 2011-02-10
What have you tried to see if the USB stick works. Installation CDs are needed for the Windows OS but as manufacturers do not usually provide drivers for Linux we rely on the Linux developers to code things to recognize all sorts of devices.

Plug in the USB stick. Boot up. And see if it is detected by Network Manager. Go to system>Administration>Additional Drivers and see if it is suggesting an available driver that you can download. I am guessing that you have wireless or wired networking already set up without the USB stick.

Make a note of any messages and information that will help others give you advice if things do not work out.

Regards and I wish you better. I hope you feel better than I did after my operation in 2009.

---

### Post by polishrose on 2011-02-11
Hi-wireless is set up and works beautifully-I didn't have to do anything-it just worked straight away. The usb stick is found in places but only as a storage device.I went into additional drivers and it says no proprietary drivers are found on the system.The usb stick lights up blue so it is finding some kind of signal.

---

### Post by herdwick on 2011-02-11
Can you determine the exact model of the USB stick (as opposed to the network it's on) eg Huawei or ZTE or similar model with number.

What version of Ubuntu ?

These 3G USB dongles start by pretending they're a CD, from which windows loads the software then flips the mode to act as a modem with various serial interfaces.

From a terminal window (Accessories, Terminal) can you do lsusb to list the devices and post the output as this will help recognise it.

---

### Post by polishrose on 2011-02-11
This is the lsusb thingy

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 10f1:1a2a  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


it's a zte model number mf626

version 10.10 maverick meerkat

---


---
title: "Enabling auto-connect for Reliance netconnect"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by ranjith19 on 2010-10-11
I have installed ubuntu 32 bit version on my HCL netbook. I use reliance netconnect (Huwai EC 1260 or 168c). I have configured it and it works well. But the only problem is that I have to connect the netconnect device before booting. If I connect it when its ON, the networkmanager does not connect automatically. 
even on the right on the tray icon, enable mobile broadband option is not there.
Please suggest solutions.
Thank you.

---

### Post by raunhar on 2010-10-21
I think that you will have to create a rule for it, so that when you plugin the device, it gets deteced.
Follow the following steps to create a rule:
Connect the device to your computer.
Terminal
lsusb
note the device position

remove the device. Write the command into terminal
sudo gksu gedit /etc/udev/rules.d/huwai_eject.rules

A blank file open sup.
Enter the following:
ACTION!="add", GOTO="3G_End"



SUBSYSTEMS=="usb", ATTRS{idProduct}=="fffd", ATTRS{idVendor}=="19d2", RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0xfffd"

LABEL="3G_End"

replace fffd and 19d2 with your device position (lsusb).

Save the file. retsart the PC and then connect the device.
It should work now.

---

### Post by ranjith19 on 2010-10-21
thanks
i will try it

---


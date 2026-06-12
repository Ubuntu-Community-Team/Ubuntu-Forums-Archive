---
title: "[SOLVED] webcam and ehci"
date: 2008-09-21
forum: Multimedia Software
---

### Post by Kheops_74 on 2008-09-21
I have a logitech Communicate Deluxe (lsusb=046d:0992 Logitech, Inc.). It works fine with skype, ekiga, cheese, flash 10, etc. The only problem is the webcam stop working some time. I think it's releted to ehci-hcd. If i stop ehci and restart it, it worka again until the next crash.

The command i use to reset echi is :
sudo modprobe -r ehci_hcd
sudo modprobe ehci-hcd

Anybody knows what is ehci-hcd?

K

---

### Post by Kheops_74 on 2008-09-23
I hope Intrepid will solve the problem. I really don't know why i must reset the usb port.

K

---

### Post by Kheops_74 on 2008-11-06
Move to Intrepid. Seems to be better.

---


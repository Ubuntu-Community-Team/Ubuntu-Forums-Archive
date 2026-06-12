---
title: "[SOLVED] Intrepid : Webcam works for time"
date: 2008-11-12
forum: Multimedia Software
---

### Post by Kheops_74 on 2008-11-12
Hi,

   My webcam works with skype, cheese, ustream (flash)... The problem is that it works one time. When a quit skype or the other software, the webcam stop working. If i reboot, it works again one time. 

Any idea? 

My webcam is a Logitech Quickcam Deluxe

Here the message in syslog

Nov 12 21:06:14 sang-desktop kernel: [51368.832132] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
Nov 12 21:06:36 sang-desktop kernel: [51390.640077] usb 6-9: reset high speed USB device using ehci_hcd and address 4
Nov 12 21:06:39 sang-desktop chipcardd[5871]: devicemanager.c: 3373: Changes in hardware list
Nov 12 21:06:51 sang-desktop kernel: [51405.788041] usb 6-9: device descriptor read/64, error -110
Nov 12 21:07:06 sang-desktop kernel: [51421.040072] usb 6-9: device descriptor read/64, error -110
Nov 12 21:07:06 sang-desktop kernel: [51421.256674] usb 6-9: reset high speed USB device using ehci_hcd and address 4
Nov 12 21:07:21 sang-desktop kernel: [51436.404555] usb 6-9: device descriptor read/64, error -110

---

### Post by Kheops_74 on 2008-11-22
I did this. It seems to work.

sudo apt-get install build-essential libsdl1.2-dev libpt-plugins-v4l2 subversion
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make
sudo modprobe -r uvcvideo
sudo make install
sudo modprobe uvcvideo
cd ..
wget [http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz)
tar -zxvf luvcview-20070512.tar.gz
cd luvcview-20070512/
make

---

### Post by Kheops_74 on 2008-11-22
Finally it doesn't work. I try this

rmmod ehci-hcd

from this post : [http://forum.ubuntu-fr.org/viewtopic.php?pid=2210721](http://forum.ubuntu-fr.org/viewtopic.php?pid=2210721)

It's better but a can't use high speed. So ustream.tv dont't work

---

### Post by Kheops_74 on 2008-11-25
rmmod ehci-hcd solve the problem for the moment. 

Any idea how i can get my webcam to work at full speed?

---


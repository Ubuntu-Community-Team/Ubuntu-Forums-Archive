---
title: "Can't get Logitech QuickCam Messenger to run on Ubuntu lucid"
date: 2010-12-12
forum: Multimedia Software
---

### Post by Snowjoggs on 2010-12-12
Got the following USB cam

```
root@enterprise:/# lsusb
Bus 005 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

```

Been trying to get it to work in ZoneMinder but its not showing any pictures.

After a couple of hours of googling the closest I have come a solution is this guide
[http://www.kuhrti.de/index.php/article/logitech-quickcam-messenger-on-ubuntu-9-04/](http://www.kuhrti.de/index.php/article/logitech-quickcam-messenger-on-ubuntu-9-04/)

Based on a custom USB driver for this cam that no longer exist [http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.8.tar.gz) 

My version infos
```
uname -a
Linux enterprise 2.6.32-26-server #48-Ubuntu SMP Wed Nov 24 10:28:32 UTC 2010 x86_64 GNU/Linux

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

```

Have anyone gotten this one to work, or have any tips for me?

---

### Post by Snowjoggs on 2010-12-12
Bit more info

dmesg info when I insert the cam

```
[  781.290032] usb 5-1: new full speed USB device using uhci_hcd and address 3
[  781.485233] usb 5-1: configuration #1 chosen from 1 choice
[  781.488195] STV06xx: Probing for a stv06xx device
[  781.488201] gspca: probing 046d:08f0
[  781.488206] STV06xx: Configuring camera
[  781.488209] STV06xx: st6422 sensor detected
[  781.488212] STV06xx: Initializing camera
[  781.773230] gspca: probe ok
[  781.773338] STV06xx: Probing for a stv06xx device
[  781.773343] gspca: probing 046d:08f0

```

I also tried fetching video directly using this method [http://www.infohit.net/blog/post/capturing-webcam-video-with-linux.html](http://www.infohit.net/blog/post/capturing-webcam-video-with-linux.html)

Then I get an error saying "VIDIOCMCAPTURE: Invalid argument"

---

### Post by no2498 on 2010-12-13
look in sound and video for cheese webcam booth
try the cam in cheese
just trying to see if it works or not

if cheese is not installed open a terminal type
sudo apt-get install cheese
click enter
password you will not see anything click enter

hope it comes on for you

---

### Post by Snowjoggs on 2010-12-13
> **no2498 said:**
> look in sound and video for cheese webcam booth
try the cam in cheese
just trying to see if it works or not

if cheese is not installed open a terminal type
sudo apt-get install cheese
click enter
password you will not see anything click enter

hope it comes on for you

Isnt cheese only for X? my server is without a monitor mind you.

---

### Post by no2498 on 2010-12-13
did not know you had no monitor

with zone minder
do you need like a web site to put the pics/video's on
i do not think its set to save to the hard drive only

---

### Post by Snowjoggs on 2010-12-13
> **no2498 said:**
> did not know you had no monitor

with zone minder
do you need like a web site to put the pics/video's on
i do not think its set to save to the hard drive only

Well yes the web interface is up and running. It just wont capture any images from my /dev/video0 device.

I was able to grap a pic through an app called webcamd now. But I would like to use it in ZM obviously.

---


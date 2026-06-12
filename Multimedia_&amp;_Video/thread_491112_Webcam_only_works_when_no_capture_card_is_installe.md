---
title: "Webcam only works when no capture card is installed.?"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by OldGaf on 2007-07-03
Hi all,

Ok, I have been fighting with a webcam for some time now and have stumbled onto an interesting situation.

I have a Quickcam Communicate and have the drivers. What I have found is that is installs and works strait away, but only if I don't have some other capture device i.e. a tvcard.

On my media system, kopete only sees the Hauppauge 500 devices. On my Web server, I only have the web cam and it works fine. Both systems are running at the same  Feisty level and both are using the same drivers.

After I run:

1) make install
2) modprobe videodev
3) modprobe quickcam

I get the following on the web server

quickcam: Registered device: /dev/video0
usbcore: registered new driver quickcam

I DO NOT get the /dev/video0 line on the media box.

I am wondering if the PVR-500 is already /dev/video0 and I need to make the webcam /dev/video1 but am not sure how to do this. 

Attached is the relevant parts of the working and not working dmesg and the drivers I am using.

Any help would be greatly appreciated.

---

### Post by OldGaf on 2007-07-03
New info added..............

---

### Post by OldGaf on 2007-07-03
bump

---


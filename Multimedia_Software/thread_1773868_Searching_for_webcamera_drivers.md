---
title: "Searching for webcamera drivers"
date: 2011-06-02
forum: Multimedia Software
---

### Post by lmf94 on 2011-06-02
I have recent started using Ubuntu 11.04, It works fine in general.
Though I miss to be able to use my webcamera, I guess the reason for this is that Ubuntu has a lack of drivers. 

So my question is, Do anyone know where I can get webcam drivers for my inbuilt webcam in Acer aspire 7730g, Crystal Eye Webcamera?

---

### Post by no2498 on 2011-06-03
open a terminal type dmesg click enter
after it stops type lsusb click inter
that should give you a number and a name for your cam



[http://www.google.com/search?client=opera&rls=en&q=Crystal+Eye+Webcamera+linux&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=Crystal+Eye+Webcamera+linux&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

---

### Post by Wobblybob on 2011-06-03
have you tried Camorama, it's in the repos and may just work out of the box, if the only program you have used is cheese then it seems to be bust at the mo.

---

### Post by lmf94 on 2011-06-05
[   23.023382] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input8
[   23.023435] usbcore: registered new interface driver uvcvideo
[   23.023437] USB Video Class driver (v0.1.0)
[   23.185891] nvidia: module license 'NVIDIA' taints kernel.
[   23.185895] Disabling lock debugging due to kernel taint
[   23.991252] Console: switching to colour frame buffer device 80x30
[   24.013395] cfg80211: World regulatory domain updated:
[   24.013398]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.013401]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.013404]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.013406]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.013408]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.013410]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


This was what I got for my webcamera when I typed what you said in the Terminal. I've tried skype, amsn, ebuddy, and other instant chat messengers (won't work at none of them).

In camorama I get this error message: Could not connect to video device (/dev/video0). Please check connection.

Edit: Installed Cheese and this works to capture images, and videos.
Though I wonder is there any method to stream the video for instant messenger programs?

---

### Post by no2498 on 2011-06-06
install the plugin flash aid for fire fox
then run it
that will give you flash player
you may need to set the sites you use in the adobe settings manager
at adobe or at the sites you use to allow and remember

---


---
title: "Failed to open video device /dev/video0"
date: 2010-03-26
forum: Multimedia Software
---

### Post by realzippy on 2010-03-26
Hi all,
have an old USB-Pencam:

```
lsusb
Bus 008 Device 003: ID 04fc:504a Sunplus Technology Co., Ltd Aiptek Mini PenCam 1.3
```

```
dmesg
[   64.570015] usb 8-1: new full speed USB device using uhci_hcd and address 3
[   64.700025] usb 8-1: device descriptor read/64, error -71
[   65.355672] usb 8-1: configuration #1 chosen from 1 choice
[   65.362553] Linux video capture interface: v2.00
[   65.363911] gspca: main v2.6.0 registered
[   65.364540] gspca: probing 04fc:504a
[   70.185157] gspca: probe ok
[   70.185229] gspca: probing 04fc:504a
[   70.185256] usbcore: registered new interface driver sunplus
[   70.185259] sunplus: registered

```

But,when opening /dev/,there is nothing,no video0 or something.
I am on Karmic.Last time I used this camera was under Edgy where I had to install *spca5xx-source* and *gspca-source*,and everything was fine....any ideas?

Digikam sees the camera:

[I]Title: Sunplus Technology Co., Ltd Aiptek Mini PenCam 1.3
Model: Aiptek Pencam
Port: usb:
Path: /
[/I]

and works,means,it can import jpeg/AVI...
Wanted to run *motion* with it,which complains:

```
[1] Failed to open video device /dev/video0: 
[1] Could not fetch initial image from camera

```

..and I need a */device/* address for the motion.conf file...

Thanks for your time..

-------------------------------------------------------------------------------------------
SOLVED!!

gspca is now integrated in the kernel,but it works only after unloading the module and reloading it while camera is plugged in...

[B]sudo modprobe -r gspca_sunplus
sudo modprobe gspca_sunplus [/B]

---

### Post by no2498 on 2010-03-26
wxcam has motion detection
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

did you try to run the gstreamer-properties see if it will set the dev video

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

hope this helps

---

### Post by sc0g on 2010-04-19
> gspca is now integrated in the kernel,but it works only after unloading the module and reloading it while camera is plugged in...

sudo modprobe -r gspca_sunplus
sudo modprobe gspca_sunplus


I'm running Ubuntu 9.10 using the PenCam as well. I can confirm that this works. Here is what I did:

1. Boot into Ubuntu... logged in.
2. Connected PenCam over USB
3. (scratch head... google.com)
4. Read this thread.
5. Ran the two commands above.
6. sudo gstreamer-properties
7. Clicked the "Video"  tab & tested my device. It works!

Thanks for figuring this out!

My lsusb output
```
Bus 004 Device 003: ID 04fc:504a Sunplus Technology Co., Ltd Aiptek Mini PenCam 1.3
```

---

### Post by tobiz on 2010-11-10
> 
[B]sudo modprobe -r gspca_sunplus
sudo modprobe gspca_sunplus [/B]
This works for me for my Philips SPC 710NC camera (gspca_sunplus replaced by gspca_sonixj) to start the microphone.  Until recently the microphone was available after boot but for some reason stopped, found this running Skype, no mic. My first work-around was under Skype to test the video which started the mic.  The modeprobe fix is better but I now need to include in the boot sequence.  I'm sure this wasn't a problem up until end of Oct 2010 (I keep my Ubuntu 10.04 system fully up to date), so what changed?

---


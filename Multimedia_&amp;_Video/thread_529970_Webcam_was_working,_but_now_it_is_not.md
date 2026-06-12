---
title: "Webcam was working, but now it is not"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by StiltonSandwich on 2007-08-19
Hi. I have a Creative PC Cam 300 webcam. This is supported by spca5xx or gspca.

Literally only a couple of weeks ago it was working perfectly, but a couple of days ago I tried to use it for the first time since then and found it not to be working - /dev/video0 is not created when I plug it in.

lsusb returns:
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 012: ID 041e:400a Creative Technology, Ltd PC-Cam 300
Bus 002 Device 001: ID 0000:0000


The only thing I can think of that has changed that might be somehow related is that I set up a USB DVB-T tuner (using the instructions at [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")) the day before I found that the webcam was not working (the tuner is not currently plugged in).

My other theory is: could this be related to a kernel upgrade? I don't remember any automatic kernel upgrades occurring, but it's all I can think of.

I've tried installing gspca and spca5xx from source from the Ubuntu repository. I don't remember how I got them last time, or whether they were supplied with Kubuntu. spca5xx fails with an error when I try to install it. gspca installs fine (with no complaints), but does not appear to work. 

When I issue modprobe gspca, I get:
FATAL: Error inserting gspca (/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/gspcav1/gspca.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Which is beyond my understanding. What does it mean; what is a "symbol"?

Here is the section of dmesg which pertains to the connection of the camera:
[22089.580000] usb 2-1: new full speed USB device using uhci_hcd and address 12
[22089.772000] usb 2-1: configuration #1 chosen from 1 choice
[22089.928000] gspca: disagrees about version of symbol video_devdata
[22089.928000] gspca: Unknown symbol video_devdata
[22089.928000] gspca: disagrees about version of symbol video_unregister_device
[22089.928000] gspca: Unknown symbol video_unregister_device
[22089.928000] gspca: disagrees about version of symbol video_device_alloc
[22089.928000] gspca: Unknown symbol video_device_alloc
[22089.928000] gspca: disagrees about version of symbol video_register_device
[22089.928000] gspca: Unknown symbol video_register_device
[22089.928000] gspca: disagrees about version of symbol video_device_release
[22089.928000] gspca: Unknown symbol video_device_release
[22090.552000] gspca: disagrees about version of symbol video_devdata
[22090.552000] gspca: Unknown symbol video_devdata
[22090.552000] gspca: disagrees about version of symbol video_unregister_device
[22090.552000] gspca: Unknown symbol video_unregister_device
[22090.552000] gspca: disagrees about version of symbol video_device_alloc
[22090.552000] gspca: Unknown symbol video_device_alloc
[22090.552000] gspca: disagrees about version of symbol video_register_device
[22090.552000] gspca: Unknown symbol video_register_device
[22090.552000] gspca: disagrees about version of symbol video_device_release
[22090.552000] gspca: Unknown symbol video_device_release

...which is rather bewildering to me.

Can anybody figure out what's wrong, and how to put it right again, please? Thank you!

---

### Post by YooDa on 2007-08-20
make sure that the "videodev" module is loaded...

sudo modprobe videodev

---

### Post by StiltonSandwich on 2007-08-20
Thanks for prompt response.

Loading videodev has no effect on the behaviour.

I'm guessing this has something to do with incompatible versions, but I wouldn't know where to begin fixing that.

---

### Post by saerguio on 2007-09-26
I've exactly the same problem.
My webcam model is Logitech QuickCam Express (lsusb says: 046d:092f ) and works fine with default ubuntu kernel drivers. But after install these ([link](http://mcentral.de/wiki/index.php/Em2880)) drivers for the
Pinnacle PCTV Hybrid Pro Stick (usb ID eb1a:2881)  the webcam doesn't work anymore.

Anyone has any tip?

---

### Post by Zweisteine on 2007-09-26
Hi,

Try building the 2.6.22.8 kernel and then the driver.
I had this problem with a ov519 camera but against 2.6.22.8 it builds & works fine.

I think the problem might be related to the kernel upgrade pushed some time ago from 2.6.20-15 to 2.6.20-16.

---

### Post by StiltonSandwich on 2007-09-26
Sorry; I kind of forgot about this thread.

Since my last post, there was, I believe, an automatic update to the kernel. This seems to have corrected the problem, which I don't doubt was caused by either the TV tuner drivers or some other driver I installed (I did install something else, but I can't remember what).

I've just tested the tuner; it still works, so if it was the drivers for that causing the problem, they've sorted themselves out.

I do wish I could understand these sorts of things.

---


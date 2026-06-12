---
title: "Camera problems: Could not claim USB device"
date: 2010-08-13
forum: Multimedia Software
---

### Post by frisket on 2010-08-13
This appears to be a frequently-asked question, but unfortunately all the answers I have been able to find are either outdated or refer to software I am not using.

[Edit: this is Lucid upgraded from Karmic on a Dell Dimension 4550]

If I plug in my antique little Kodak EZ-200, it appears to be recognised; that is, /var/log/messages says:

Aug 13 23:40:47 adam kernel: [ 9628.980041] usb 3-1: new full speed USB device using uhci_hcd and address 2
Aug 13 23:40:47 adam kernel: [ 9629.177161] usb 3-1: configuration #1 chosen from 1 choice
Aug 13 23:40:48 adam kernel: [ 9630.093358] Linux video capture interface: v2.00
Aug 13 23:40:48 adam kernel: [ 9630.149510] gspca: main v2.7.0 registered
Aug 13 23:40:48 adam kernel: [ 9630.275929] gspca: probing 040a:0300
Aug 13 23:40:48 adam kernel: [ 9630.277908] gspca: probe ok
Aug 13 23:40:48 adam kernel: [ 9630.277937] gspca: probing 040a:0300
Aug 13 23:40:48 adam kernel: [ 9630.277987] usbcore: registered new interface driver spca500
Aug 13 23:40:48 adam kernel: [ 9630.278532] spca500: registered
Aug 13 23:40:50 adam kernel: [ 9631.898871] gspca: disconnect complete

lsusb seems to confirm this:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 040a:0300 Kodak Co. EZ-200
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 03f0:2612 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

But gphoto2 --auto-detect -L says:

Model                          Port                                            
----------------------------------------------------------
Kodak EZ200                    usb:            

*** Error ***              
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (No such file or directory). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

How do I find out what module has claimed the camera, and permanently remove it or prevent it from ever doing so again?

Is there some method of telling gphoto2 (or any other camera-handling program) to stamp all over anything else that has laid claim to a device and brute-force its way?

---

### Post by no2498 on 2010-08-14
? not an answer have you installed the program motion
it runs all the time if you have it installed you need to stop it

same with any chat/cam programs, skype, msn, ekiga, an so on

try the cam in cheese webcam booth
look in sound and video for it

btw cheese has a good help file look in the faq's

hope this helps

---

### Post by chriswhat21 on 2010-08-19
I've been messing with my EZ200 every few months.  I found this "sudo killall gvfs-gphoto2-volume-monitor" on [http://ubuntuforums.org/showthread.php?t=1163070&highlight=gphoto+usb](http://ubuntuforums.org/showthread.php?t=1163070&highlight=gphoto+usb) thread.  I unplugged the camera,  ran that in terminal, opened F-Spot, plugged in the camera, and Imported.  It copied the pictures, all messed up, then froze.  I'm still looking though.

---

### Post by frisket on 2010-08-23
> **no2498 said:**
> ? not an answer have you installed the program motion
it runs all the time if you have it installed you need to stop it
same with any chat/cam programs, skype, msn, ekiga, an so on

No, some of these are installed but not running.

> **no2498 said:**
> try the cam in cheese webcam booth
look in sound and video for it
btw cheese has a good help file look in the faq's
hope this helps

Cheese says no device found, same as everything else.

---

### Post by frisket on 2010-08-23
> **chriswhat21 said:**
> I've been messing with my EZ200 every few months.  I found this "sudo killall gvfs-gphoto2-volume-monitor" on [http://ubuntuforums.org/showthread.php?t=1163070&highlight=gphoto+usb](http://ubuntuforums.org/showthread.php?t=1163070&highlight=gphoto+usb) thread.  I unplugged the camera,  ran that in terminal, opened F-Spot, plugged in the camera, and Imported.  It copied the pictures, all messed up, then froze.  I'm still looking though.

Thanks for the link. I ran the command, plugged in, ran F-Spot and it imported all the files, then hung. The files are indeed completely garbage (the same garbage as they were under all previous versions of Ubuntu and <whatever-driver> that F-Spot, gphoto2, etc are using for the EZ200. 

Basically, getting round the lock on the USB is great, but the driver used to download the images is fatally broken.

---

### Post by chriswhat21 on 2010-08-28
Wow, don't believe I didn't check it before.  I unplugged, ran "sudo killall gvfs-gphoto2-volume-monitor" plugged in, ran cheese, and IT WORKS!!!  So crazy that I didn't check that before.  Now the copy problem...any help?

---


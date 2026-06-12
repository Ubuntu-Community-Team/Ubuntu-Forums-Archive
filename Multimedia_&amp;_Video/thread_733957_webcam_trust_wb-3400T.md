---
title: "webcam trust wb-3400T"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by Marafarrico on 2008-03-24
Hello all,

I'm trying to install my trust wb-3400t webcam and after looking in many posts I wasn't able to do it. Some ask for the gspca, other for Snc9 and either with one or another at the end I can't create the /dev/video0 (or /dev/video1?) even if the light of the cam is on.

I'm using Ubuntu 7.10 (Gutsy)

the result of lsusb is

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 093a:2600 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  

the result of dmesg | grep usb is

[   21.639975] usbcore: registered new interface driver usbfs
[   21.640011] usbcore: registered new interface driver hub
[   21.640035] usbcore: registered new device driver usb
[   21.641735] usb usb1: configuration #1 chosen from 1 choice
[   21.743690] usb usb2: configuration #1 chosen from 1 choice
[   21.847480] usb usb3: configuration #1 chosen from 1 choice
[    3.892000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    4.100000] usb 1-2: configuration #1 chosen from 1 choice
[    6.012000] usb usb4: configuration #1 chosen from 1 choice
[    6.040000]  hdd:<6>usb 1-2: USB disconnect, address 2
[    6.788000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    6.996000] usb 1-2: configuration #1 chosen from 1 choice
[   19.740000] usbcore: registered new interface driver gspca

Can any one help me?
Thanks!

---

### Post by linuxwizard on 2008-03-24
Have you just tried using your webcam with any apps. to see if it would work ? Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. (should be v4l2)
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing.

---

### Post by Marafarrico on 2008-03-24
Hi,
I forgot to say that I've tryed with Skype, amsn, Ekiga and camorama. In summary something like "can not detect video device /dev/video" is shown.  Sorry for that.

Also, even if it doesn't show up in the webcam requirements, let me just add that I only have got a 1MB video card.

My "feeling" is that when the driver's installation is done the dev/video/ isn't created as it was supposed to, or else, when the video apps are started, they go to search for this "dev" somewhere else. But this is just a naive guess.

Any help more? 
Thank you in advance.

---

### Post by linuxwizard on 2008-03-24
Camorama does not support v4l2 so it will not work with your cam. Your cam is list here > [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) > you need the lastest version of gspca for the cam to work. If you have already installed the newest version have you rebooted your computer ? In Ekiga make sure your settings are set to  v4l2 like I stated in my earlier post.

---

### Post by Marafarrico on 2008-03-24
I've reinstaled the gspca-source (the only available) using synaptic. Rebooted and then in the window Preferences of Ekiga, tryed to detect a video device with v4l2, v4l and with different channels. The light of the cam is on but it can't detected anything.
I note that, while following other post, I've also installed gspcav1-20071224. 

Thanks a lot for your help!

---

### Post by linuxwizard on 2008-03-24
Post results of this command > lsmod | grep videodev  >>this will show driver your webcam is using to make sure it is using correct driver.

---

### Post by Marafarrico on 2008-03-24
This are the results of lsmod | grep videodev

videodev               29312  1 gspca
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev


Also when using  xawtv
"
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
xinerama 0: 800x600+0+0

WARNING: No DGA support available for this display.

can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No existe el fichero ó directorio
v4l2: open /dev/video0: No existe el fichero ó directorio
v4l: open /dev/video0: No existe el fichero ó directorio
no video grabber device available
"

---

### Post by Marafarrico on 2008-03-27
The funny thing is that using this tutorial
[http://albertjh.cymaho.com/?p=8](http://albertjh.cymaho.com/?p=8)
at work, also with Ubuntu 7.10 everything goes ok, but not with my home pc.
Any help?

---

### Post by atpat on 2008-06-13
I'm reawakening this thread as I'm having an almost identical problem on v8.04..

dmesg output:
[   16.553442] usbcore: registered new interface driver usbhid
[   16.553446] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  897.817971] usb 2-2: new full speed USB device using uhci_hcd and address 3
[  897.976278] usb 2-2: configuration #1 chosen from 1 choice
[  385.293314] usbcore: registered new interface driver snd-usb-audio
[  385.361882] usb 2-2: SN9C103 PC Camera Controller detected (vid:pid 0x0C45:0x60AF)
[  385.438780] usb 2-2: PAS202BCB image sensor detected
[  338.091631] usb 2-2: Initialization succeeded
[  338.091668] usb 2-2: V4L2 device registered as /dev/video0
[  338.091671] usb 2-2: Optional device control through 'sysfs' interface disabled
[  338.091691] usbcore: registered new interface driver sn9c102
[ 1002.610084] usb 2-2: usb_submit_urb() failed, error -28
(that last line repeats about 15 times).

So the driver being used is sn9c102.  The dev/video0 **does** exist.

lsusb output:
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0c45:60af Microdia 
Bus 002 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

I did look at the information about Microdia, but got thoroughly scared off by the idea of recompiling the kernal.  Sorry; but from what I can tell the correct driver is already part of 8.04.

lsmod output:
videodev               29440  1 sn9c102
v4l1_compat            15492  1 videodev
v4l2_common            18304  2 sn9c102,videodev

I've tried in Skype, Camorama and Ekiga.  In each it reports that no camera device is present.

I also note [this thread]("http://ubuntuforums.org/showthread.php?t=346338") and [this howto]("http://ubuntuforums.org/showthread.php?t=75284") but, noting that there are differences in the procedure for Breezy and Dapper/Edgy, there may be further differences for v8 and I don't know enough yet to tell.

So, has anyone actually worked out WHY THIS HAPPENS and whether anything can be done about it which does not involve recompiling the kernal?

---


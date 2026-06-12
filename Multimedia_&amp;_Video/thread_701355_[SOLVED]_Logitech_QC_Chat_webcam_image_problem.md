---
title: "[SOLVED] Logitech QC Chat webcam image problem"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by koetjeboeh on 2008-02-19
Hi all,

have a problem with my QC Chat. Webcam works, at least gives output, images are not correct. See this link:

[http://www.tigru.nl/pics/webcam.jpeg](http://www.tigru.nl/pics/webcam.jpeg)

Image is created with webcam using input = SPCA561, part of xawtv.

First some information

~$ uname -r
2.6.22-14-386

~$ lsusb
Bus 001 Device 003: ID 1631:5000
Bus 001 Device 002: ID 046d:092e Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

~$ lsmod |grep spca
gspca                 678992  1
videodev               28288  2 gspca
usbcore               136088  4 gspca,usbhid,uhci_hcd

dmseg gives a lot of output, there are the last rows

~$ dmesg | grep spca
[16487.072000] /usr/src/gspcav1-20071224/Sunplus/spca561.h: [spca561_init:467] Find spca561 USB Product ID 92e
[16487.144000] /usr/src/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
[16487.144000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
[16487.152000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.152000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 6
[16487.160000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.160000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 5
[16487.168000] /usr/src/gspcav1-20071224/gspca_core.c: [spca5xx_do_ioctl:2124] Bridge SPCA561
[16487.172000] /usr/src/gspcav1-20071224/gspca_core.c: [spca5xx_do_ioctl:2124] Bridge SPCA561
[16487.176000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
[16487.184000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.184000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 6
[16487.192000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.192000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 5
[16487.300000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
[16487.308000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.308000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 6
[16487.316000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.316000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 5

Is this any way related to the driver? Anybody seen this problem and has a solution or hint?

Regards,
Fabio

---

### Post by linuxwizard on 2008-02-19
Have you tried using your webcam with Ekiga, Camorama, or  Cheese ? I have the same webcam mine works fine in all of these. As long as I have good lighting in the room I am in or their will be a red tint to it.. I don't use xawtv, mightbe a issue there.

---

### Post by koetjeboeh on 2008-02-19
> **linuxwizard said:**
> Have you tried using your webcam with Ekiga, Camorama, or  Cheese ? I have the same webcam mine works fine in all of these. As long as I have good lighting in the room I am in or their will be a red tint to it.. I don't use xawtv, mightbe a issue there.

Hi linuxwizard,

None of those tools. It is a noscreen server pc. So I am limited to command line webcam tools. There are quite some though, and in all the webcam seems to work(even streaming with webcam-server), but the quality is poor, unusable, like the one in the above link.

Regards,
Fabio

---

### Post by koetjeboeh on 2008-02-21
> **koetjeboeh said:**
> Hi all,

have a problem with my QC Chat. Webcam works, at least gives output, images are not correct. See this link:

[http://www.tigru.nl/pics/webcam.jpeg](http://www.tigru.nl/pics/webcam.jpeg)

Image is created with webcam using input = SPCA561, part of xawtv.

First some information

~$ uname -r
2.6.22-14-386

~$ lsusb
Bus 001 Device 003: ID 1631:5000
Bus 001 Device 002: ID 046d:092e Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

~$ lsmod |grep spca
gspca                 678992  1
videodev               28288  2 gspca
usbcore               136088  4 gspca,usbhid,uhci_hcd

dmseg gives a lot of output, there are the last rows

~$ dmesg | grep spca
[16487.072000] /usr/src/gspcav1-20071224/Sunplus/spca561.h: [spca561_init:467] Find spca561 USB Product ID 92e
[16487.144000] /usr/src/gspcav1-20071224/gspca_core.c: [spca5xx_set_light_freq:1932] Sensor currently not support light frequency banding filters.
[16487.144000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
[16487.152000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.152000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 6
[16487.160000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.160000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 5
[16487.168000] /usr/src/gspcav1-20071224/gspca_core.c: [spca5xx_do_ioctl:2124] Bridge SPCA561
[16487.172000] /usr/src/gspcav1-20071224/gspca_core.c: [spca5xx_do_ioctl:2124] Bridge SPCA561
[16487.176000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
[16487.184000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.184000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 6
[16487.192000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.192000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 5
[16487.300000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7
[16487.308000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.308000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 6
[16487.316000] /usr/src/gspcav1-20071224/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
[16487.316000] /usr/src/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 5

Is this any way related to the driver? Anybody seen this problem and has a solution or hint?

Regards,
Fabio

I've received some information from an other useful forum, for Logitech devices, the QuickCam Team([http://forums.quickcamteam.net](http://forums.quickcamteam.net)). See thread [http://forums.quickcamteam.net/showthread.php?tid=184](http://forums.quickcamteam.net/showthread.php?tid=184).

Basically the logging said that there wasn't sufficient bandwidth for the cam to work(error -28 ("No space left on device")). This seems odd, however when I unplugged my other USB device(a never used keyboard) on this machine, the cam started working. So the logging made sense. It is not clear to me if this is related to a broken USB device or USB card. Will look into that if I have some time.
The problem is solved.

Thanks for your input.

Regards,
Fabio

---


---
title: "[SOLVED] Webcam not working SPCA5XX"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by nikolay28 on 2007-11-28
Hello Folks im Stuck with a problem. :(
I bought a Trust webcam which si not working under
Ubuntu 7.10

I give you som enviroment infos so may be you can help me.

Ubuntu 7.10 
laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux 

[ 3877.404000] usb 2-2: USB disconnect, address 8 
[ 3881.948000] usb 2-1: new full speed USB device using uhci_hcd and address 9 
[ 3882.180000] usb 2-1: configuration #1 chosen from 1 choice 
[ 3882.184000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. (PAC207) 

lsmod | grep gspca 
gspca 608336 0 
videodev 29312 1 gspca 
usbcore 138632 4 gspca,ehci_hcd,uhci_hcd 

ls -al /dev/video0 
crw-rw---- 1 root video 81, 0 2007-11-26 20:44 /dev/video0 

video:44:silvie,niko 

So the web cam is recogniced from the system an a /dev/video is created,
but I can not connect to the device :(

So Please Help me to get arount that problem,

Thank you

---

### Post by seeklinux on 2007-11-28
Try [this site]("http://mxhaard.free.fr/spca5xx.html").

---

### Post by nikolay28 on 2007-11-29
Thank you for overwhelming long answer :-)
I have tried the driver from the page, where you gave me the link but still no luck :-(
As i mentioned before the camera is recognized by the system an the module
is loaded. But still no luck to connect to the /dev/video0 device

---

### Post by seeklinux on 2007-11-29
Sorry about the short answer. It has been quite a while since I worked on the issue. I just remember finding the driver at the site I mentioned and using it to solve the problem I had with my webcam (which is different from yours, but uses that driver). 

In my case, the lsmod command gives:

 lsmod | grep gspca
gspca                 608336  0 
videodev               29312  1 gspca
usbcore               138632  7 snd_usb_audio,snd_usb_lib,gspca,hci_usb,ehci_hcd,uhci_hcd

You may want to see if you can use the SpcaView or SpcaTools at that site to help you diagnose the problem. I noticed that the compatibility chart mentioned LE for the Trust camera. Not sure if you need to do something different for the light edition.

By the way, once I got the camera to work, I used gqcam with the driver. With some other programs, the colors were wrong.

---

### Post by damir_1105 on 2007-12-01
> **nikolay28 said:**
> Hello Folks im Stuck with a problem. :(
I bought a Trust webcam which si not working under
Ubuntu 7.10

I give you som enviroment infos so may be you can help me.

Ubuntu 7.10 
laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux 

[ 3877.404000] usb 2-2: USB disconnect, address 8 
[ 3881.948000] usb 2-1: new full speed USB device using uhci_hcd and address 9 
[ 3882.180000] usb 2-1: configuration #1 chosen from 1 choice 
[ 3882.184000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. (PAC207) 

lsmod | grep gspca 
gspca 608336 0 
videodev 29312 1 gspca 
usbcore 138632 4 gspca,ehci_hcd,uhci_hcd 

ls -al /dev/video0 
crw-rw---- 1 root video 81, 0 2007-11-26 20:44 /dev/video0 

video:44:silvie,niko 

So the web cam is recogniced from the system an a /dev/video is created,
but I can not connect to the device :(

So Please Help me to get arount that problem,

Thank you

try this: [http://ubuntuforums.org/showthread.php?t=595924&highlight=trust+webcam]("http://ubuntuforums.org/showthread.php?t=595924&highlight=trust+webcam")

---

### Post by nikolay28 on 2007-12-05
Thank you for the link,
now it works :)

I have to copy the gspca.ko file to

/lib/modules//kernel/drivers/usb/media/
/lib/modules/ubuntu/media/gspcav1/

then rmmod gspca

plug in the camera again and then hurray it works :-D

---


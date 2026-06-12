---
title: "Logitech Clicksmart 310 doesn't work"
date: 2009-12-19
forum: Multimedia Software
---

### Post by ununseptium on 2009-12-19
Hi!

I want to use my *Logitech Clicksmart 310* with Karmic Koala. But when the webcam is plugged in, there is no **/dev/video0**. So e.g. Camorama can't display anything.

This is the [FONT=Courier New]dmesg[/FONT] output:
```
[18599.912126] usb 5-2: new full speed USB device using uhci_hcd and address 3
[18600.080164] usb 5-2: configuration #1 chosen from 1 choice
[18600.152790] Linux video capture interface: v2.00
[18600.161538] gspca: main v2.6.0 registered
[18600.186557] gspca: probing 046d:0900
[18600.204593] gspca: probe ok
[18600.204613] gspca: probing 046d:0900
[18600.204653] usbcore: registered new interface driver spca500
[18600.204660] spca500: registered
[18600.470727] gspca: disconnect complete
```When using Ubuntu 8.10, the webcam worked after unchecking *apps &#8594; nautilus &#8594; preferences &#8594; media_automount* in gconf-editor ([https://bugs.launchpad.net/ubuntu/+bug/297594](https://bugs.launchpad.net/ubuntu/+bug/297594)). But this doesn't solve it any more. The current problem seems to be different, because there is no error message when plugging in, unlike the problem with Ubuntu 8.10.

It would be great, if somebody could help me. :)

---

### Post by heltoupee on 2010-02-19
Same exact problem here.  Have not been able to find any helpful resolution except for "buy one of these other cameras".  Oh well.  my dmesg (which looks surprisingly like yours :)  ) is below.

[526547.262544] usb 2-1: new full speed USB device using ohci_hcd and address 3
[526547.482178] usb 2-1: configuration #1 chosen from 1 choice
[526548.442486] Linux video capture interface: v2.00
[526548.488869] gspca: main v2.6.0 registered
[526548.491867] gspca: probing 046d:0900
[526548.538130] gspca: probe ok
[526548.538180] gspca: probing 046d:0900
[526548.538227] usbcore: registered new interface driver spca500
[526548.538234] spca500: registered
[526549.020441] gspca: disconnect complete

---

### Post by CrIpPeN on 2010-03-10
I got the same problem, same camera to ClickSmart 310

---

### Post by swlazlowski on 2010-04-04
What works for me is:
```
modprobe -r gspca_spca500 && sleep 60s && modprobe gspca_spca500
```

still trying to set it up in rc.local at boot time or when camera connected. Let me know if it helps.

---

### Post by manzuk on 2010-05-28
That worked for me! Weird...
It seems the problem comes up when connecting the cam (I have a Creative PC CAM 300).

---

### Post by sae.area on 2011-02-06
Hi,

the Logitech ClickSmart 310 can be used as stand-alone camera or as webcam. I think because of this feature mix, Linux tries to connect to it as stand-alone camera trying to access the storage media where the pictures are stored. Since that attempt fails it disconnects the camera. In the following bug report ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678)) a user suggested to black list this camera in some module which tries to load access the storage media. I guess then the disconnect wouldn't happen.
Another workaround to get the camera working is the following:
before plugging in the webcam I kill:
/usr/lib/gvfs/gvfs-gphoto2-volume-monitor
But this monitor gets reloaded after a while and the camera is disconnected again (if I remember correctly).

---


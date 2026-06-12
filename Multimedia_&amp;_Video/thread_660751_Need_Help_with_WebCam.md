---
title: "Need Help with WebCam"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by Linux Loser on 2008-01-07
Well, I'm new to Linux and I wanted to use a Philips webcam that I purchased.
I noticed that I cannot install the camera with the installation cd. I plugged it in, thinking maybe it would auto-detect, and nothing happened. 

I am a noob at this and I have no idea what I am doing. But, how do I install my web camera?

---

### Post by scizzo on 2008-01-07
Is this a USB webcam?

What does

```
tail -f /var/log/syslog
```

and

```
dmesg
```

tell you when you plug in the camera?

Also which camera is it?

---

### Post by BELLION on 2008-01-07
I have an entegred camera Lg smart cam does anyone know where I can find the driver..

---

### Post by Linux Loser on 2008-01-07
It is a Usb Camera.

heres what it says when i do the first code.

> Jan  7 15:25:20 Laptop dhclient: bound to 192.168.0.6 -- renewal in 40642 seconds.
Jan  7 15:25:20 Laptop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface ath0 
Jan  7 15:39:30 Laptop -- MARK --
Jan  7 15:50:26 Laptop kernel: [40273.928000] usb 3-1: new full speed USB device using uhci_hcd and address 3
Jan  7 15:50:26 Laptop kernel: [40274.188000] usb 3-1: configuration #1 chosen from 1 choice
Jan  7 15:50:26 Laptop kernel: [40274.192000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
Jan  7 15:50:26 Laptop NetworkManager: <debug> [1199739026.856539] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_561_noserial'). 
Jan  7 15:50:26 Laptop NetworkManager: <debug> [1199739026.937906] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Jan  7 15:50:26 Laptop NetworkManager: <debug> [1199739026.939283] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_561_noserial_video4linux'). 
Jan  7 15:50:26 Laptop NetworkManager: <debug> [1199739026.951009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4fc_561_noserial_usbraw').

And heres what it says on the dmesg thing

> [  786.016000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  786.220000] usb 3-1: configuration #1 chosen from 1 choice
[  786.280000] Linux video capture interface: v2.00
[  786.300000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[  786.304000] usbcore: registered new interface driver gspca
[  786.304000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[  896.660000] usb 3-1: USB disconnect, address 2
[ 1153.960000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 1154.164000] usb 2-1: configuration #1 chosen from 1 choice
[ 1154.168000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[ 1429.028000] usb 2-1: USB disconnect, address 2
[40273.928000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[40274.188000] usb 3-1: configuration #1 chosen from 1 choice
[40274.192000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)


There was more, but it was way too long.

It doesnt do anything when i plug in the camera.

And the box doesnt tell me what kind of camera it is. It just says Philips Pc Camera SCI4750/27.

---

### Post by Steveway on 2008-01-07
> [ 786.280000] Linux video capture interface: v2.00
[ 786.300000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[ 786.304000] usbcore: registered new interface driver gspca
[ 786.304000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
Sounds good. It seems that your system detected the camera and enabled the gspca driver for you.
Did you test the camera? There is an app called Cheese in the repositories, you can use that to test the camera.
(I have a camera that uses gspca myself, and it just works.)

---

### Post by Linux Loser on 2008-01-07
Ok thank you \\:D/

---

### Post by zarad ZARAD on 2008-02-25
I Need  To All   Driver  To  Lg E500-l.a2abe   For  Win  Xp
And Driver  Smart Cam    
Thank  You

---


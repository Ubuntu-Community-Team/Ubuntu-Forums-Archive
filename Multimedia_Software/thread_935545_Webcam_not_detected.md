---
title: "Webcam not detected"
date: 2008-10-01
forum: Multimedia Software
---

### Post by buntute on 2008-10-01
Hello, I tried to use a new webcam Orlens from Smart Technology with ubuntu Hardy, but not detected even in lsusb.

```
warnet@ubuntu:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
warnet@ubuntu:~$ 

```

Below is dmesg output :
```
warnet@ubuntu:~$ dmesg | grep usb
[   72.434104] usbcore: registered new interface driver usbfs
[   72.434154] usbcore: registered new interface driver hub
[   72.490272] usbcore: registered new device driver usb
[   72.541648] usb usb1: configuration #1 chosen from 1 choice
[   72.642708] usb usb2: configuration #1 chosen from 1 choice
[   72.746685] usb usb3: configuration #1 chosen from 1 choice
[   72.882041] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   73.001975] usb 1-1: device descriptor read/64, error -71
[   73.225868] usb 1-1: device descriptor read/64, error -71
[   73.441752] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   73.565641] usb 1-1: device descriptor read/64, error -71
[   73.789524] usb 1-1: device descriptor read/64, error -71
[   74.005439] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   74.421161] usb 1-1: device not accepting address 4, error -71
[   74.533171] usb 1-1: new full speed USB device using uhci_hcd and address 5
[   74.952859] usb 1-1: device not accepting address 5, error -71
[  103.725266] usb 1-1: new full speed USB device using uhci_hcd and address 6
[  103.849228] usb 1-1: device descriptor read/64, error -71
[  104.077060] usb 1-1: device descriptor read/64, error -71
[  104.292940] usb 1-1: new full speed USB device using uhci_hcd and address 7
[  104.412886] usb 1-1: device descriptor read/64, error -71
[  104.636757] usb 1-1: device descriptor read/64, error -71
[  104.852646] usb 1-1: new full speed USB device using uhci_hcd and address 8
[  105.260422] usb 1-1: device not accepting address 8, error -71
[  105.372364] usb 1-1: new full speed USB device using uhci_hcd and address 9
[  105.788146] usb 1-1: device not accepting address 9, error -71
[  198.405853] usb 1-1: new full speed USB device using uhci_hcd and address 10
[  198.529825] usb 1-1: device descriptor read/64, error -71
[  198.753707] usb 1-1: device descriptor read/64, error -71
[  198.969607] usb 1-1: new full speed USB device using uhci_hcd and address 11
[  199.089533] usb 1-1: device descriptor read/64, error -71
[  199.313484] usb 1-1: device descriptor read/64, error -71
[  199.529316] usb 1-1: new full speed USB device using uhci_hcd and address 12
[  199.937116] usb 1-1: device not accepting address 12, error -71
[  200.049058] usb 1-1: new full speed USB device using uhci_hcd and address 13
[  200.456867] usb 1-1: device not accepting address 13, error -71
warnet@ubuntu:~$ 


```

Anyone can help ?

---

### Post by buntute on 2008-10-02
Hello, anyone can help ?

---

### Post by buntute on 2008-10-02
Hello, any help ?

---

### Post by patrickballeux on 2008-10-02
From your logs, your first problem is that Ubuntu is unable to give an adress to your webcam.

Is it plugged into a hub, or do you have a lot of usb devices connected?  Try unpluggin everything and leave only your webcam.  Then check what the kernel says when you plug/unplug.

Until the kernel is able to talk to it, no driver/module would make it work.

---

### Post by buntute on 2008-10-03
Hi, thanks for come up with reply.

Btw, I have only Webcam with USB, no other USB is used. And I have tried to plug - unplug, restart, remove ehci as I googled it could be the solution, but nothing was worked.

How to check the kernel says ?

Please advise.

---

### Post by buntute on 2008-10-03
I just tried to plug again, and look into the syslog kern.log, here is the logs :
```
Oct  3 20:02:40 ubuntu kernel: [ 5859.998275] usb 1-1: device descriptor read/64, error -71
Oct  3 20:02:41 ubuntu kernel: [ 5860.222168] usb 1-1: device descriptor read/64, error -71
Oct  3 20:02:41 ubuntu kernel: [ 5860.438055] usb 1-1: new full speed USB device using uhci_hcd and address 4
Oct  3 20:02:41 ubuntu kernel: [ 5860.557997] usb 1-1: device descriptor read/64, error -71
Oct  3 20:02:41 ubuntu kernel: [ 5860.781930] usb 1-1: device descriptor read/64, error -71
Oct  3 20:02:41 ubuntu kernel: [ 5860.997822] usb 1-1: new full speed USB device using uhci_hcd and address 5
Oct  3 20:02:42 ubuntu kernel: [ 5861.405573] usb 1-1: device not accepting address 5, error -71
Oct  3 20:02:42 ubuntu kernel: [ 5861.517546] usb 1-1: new full speed USB device using uhci_hcd and address 6
Oct  3 20:02:42 ubuntu kernel: [ 5861.925321] usb 1-1: device not accepting address 6, error -71
```

Any advise ?

---

### Post by patrickballeux on 2008-10-03
Can you check it in a Windows setup to see if it works?

The problem is that the webcam is simply not recognized because it is not responding in a standard way.  I think there is no hope for this webcam.  If the kernel is unable to connect to it, you won't be able to go any further...

My best advice, get another webcam, they are cheap (Get a logitech, they work great).

You webcam is broken or it is a really strange brand.

Just an idea like that, can you check with another webcam just to validate that the problem is not your usb controller or your setup?

---

### Post by buntute on 2008-10-03
.

---

### Post by buntute on 2008-10-03
Hi, thanks Patrick. Yes, I would try your suggestion to get another webcam if any efforts fails.

I have no Windows machine right now, so I just tried plug the webcam to another machine with Ubuntu Gutsy, it has detected as 17a1:0128 with no name.

```
warmin@edubuntu:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 005 Device 002: ID 17a1:0128  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
warmin@edubuntu:~$ 

```

In the syslog :
```
Oct  4 10:00:15 edubuntu NetworkManager: <debug> [1223089215.514521] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_17a1_128_noserial'). 
Oct  4 10:00:15 edubuntu NetworkManager: <debug> [1223089215.589601] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_17a1_128_noserial_if0'). 
Oct  4 10:00:15 edubuntu NetworkManager: <debug> [1223089215.619722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_17a1_128_noserial_usbraw'). 
```

Is it meaned something ?

---

### Post by gali98 on 2008-10-03
hmmm... This means that something is wrong on the software side of the hardy box (probably)
Could you upload the file 
/boot/grub/menu.lst
And what kind of computer do you have?
If it is little known or a custom, what kind of motherboard do you have?
Kory

---

### Post by buntute on 2008-10-03
and the dmesg :
```
warmin@edubuntu:~$ dmesg | grep usb
[   24.756181] usbcore: registered new interface driver usbfs
[   24.756220] usbcore: registered new interface driver hub
[   24.756253] usbcore: registered new device driver usb
[   25.801794] usb usb1: configuration #1 chosen from 1 choice
[   25.902952] usb usb2: configuration #1 chosen from 1 choice
[   26.006736] usb usb3: configuration #1 chosen from 1 choice
[   26.110626] usb usb4: configuration #1 chosen from 1 choice
[   26.214501] usb usb5: configuration #1 chosen from 1 choice
[   26.565843] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   26.742159] usb 2-2: configuration #1 chosen from 1 choice
[   26.981495] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   27.153659] usb 3-1: configuration #1 chosen from 1 choice
[   33.140583] usbcore: registered new interface driver hiddev
[   33.164447] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2
[   33.164468] usbcore: registered new interface driver usbhid
[   33.164473] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[ 2265.552961] usb 5-1: new full speed USB device using uhci_hcd and address 2
[ 2265.723939] usb 5-1: configuration #1 chosen from 1 choice
warmin@edubuntu:~$ 

```

But camorama still not work with this... the error message appeared :
```
Could not connect to video device (/dev/video0). Please check connection
```

---

### Post by gali98 on 2008-10-03
you may have missed my post. Check on the first page...
Kory
edit: on the gusty machine, install the package luvcview
and see if the webcam works.
Kory

---

### Post by Crafty Kisses on 2008-10-04
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by buntute on 2008-10-04
Hi Kory and Codename,

Sorry, and yes, I've been missed your first post in page 1.

I cannot install luvcview in gutsy, see below :
```
warmin@edubuntu:~$ sudo apt-get install luvcview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package luvcview
warmin@edubuntu:~$ 

```

Right now I'm not at home and still in gutsy, my hardy is at home, I'd try to check with the hardy machine again later.
The gutsy has ASUS motherboard, not sure with the model yet.

Unfortunately, at the second plug of the device, it was not detected again in gutsy. I recalled that I also met this event in Hardy, only first plug detected the device but with no name.
```
warmin@edubuntu:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
warmin@edubuntu:~$ 

```

When use Ekiga, I saw the Ekiga logo bouncing slowly.

---

### Post by buntute on 2008-10-11
Hi,

Sorry for so long, just want to update this thread, finally I got to change the webcam, because after 've been checked with Windows computer, the webcam was also not able to work.

Thanks anyway for all your responses and helps.

---


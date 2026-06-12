---
title: "[SOLVED] Panasonic DMC-FX12 Photo camera"
date: 2008-05-23
forum: Multimedia Software
---

### Post by jeroenvrp on 2008-05-23
Hello,

I installed Kubuntu Hardy for a good friend of mine. All works great, except one major thing not: his digital photo camera.

It's a Panasonic DMC-FX12. When I connect the camera it is recognized and I can choose between Digikam or opening it in Konqueror.

When opening in Konqueror it is mounted, but there is nothing in there.

When opening in Digikam it takes a while and it says it can't connect. It sees the amount of free and used space on the camera.

Please help?

---

### Post by jeroenvrp on 2008-05-24
Just one more thing: 

In Linux the camera display says: "Connected to the PC" and on Windows it goes one step further by saying: "Access".

---

### Post by IgnorantGuru on 2008-05-24
> When I connect the camera it is recognized and I can choose between Digikam or opening it in Konqueror.

In my experience with the Panasonic TZ3, it will be recognized twice - as a camera and as a mass storage device (two independent prompts will open asking me to choose what to open it with).  If it's being recognized as a camera only, that could be why konqueror is coming up blank.  See if it says "camera".  I would check to see if the camera has a setting for PC mode - MSD/DCIM vs PTP/Pictbridge.

Also, I found that putting the card into a card reader provides much faster transfers than the USB cable, so you could consider getting a card reader as a workaround.

And my camera does say connected to PC whenever it is hooked up.  It adds "Access" only when actively writing/reading data.

---

### Post by xc3RnbFO8P on 2008-05-24
Try KPhotoAlbum in Add/Remove (All Available Application)

---

### Post by jeroenvrp on 2008-05-29
Unfortunately the camera has no option to set a pc mode or such. According the listing on the website of gphoto2, the camera-series where this one belongs to, is supported. It just should work with USB Mass Storage.

I found this in /var/log/kern.log:


```
May 29 18:14:22 k-uptown kernel: [56955.444988] usb 3-2: new full speed USB device using uhci_hcd and address 9
May 29 18:14:22 k-uptown kernel: [56955.613217] usb 3-2: configuration #1 chosen from 1 choice
May 29 18:14:22 k-uptown kernel: [56955.630216] scsi9 : SCSI emulation for USB Mass Storage devices
May 29 18:14:22 k-uptown kernel: [56955.635198] usb-storage: device found at 9
May 29 18:14:22 k-uptown kernel: [56955.635207] usb-storage: waiting for device to settle before scanning
May 29 18:14:49 k-uptown kernel: [56982.182342] usb 3-2: usbfs: USBDEVFS_CONTROL failed cmd kio_kamera rqt 33 rq 102 l
en 0 ret -71
```

Seems like the last line is the one where it's all about. 

Please help?

---

### Post by jeroenvrp on 2008-05-29
When I do a sudo /etc/init.d/hal stop

and do it mount manually:

```
sudo mkdir /media/camera
sudo mount /dev/sdc1 /media/camera
```

It works, also in Digikam with Directory Browse.

I get those ideas from this thread: [http://forums.suselinuxsupport.de/lofiversion/index.php/t59707.html](http://forums.suselinuxsupport.de/lofiversion/index.php/t59707.html)

So this has properly to do with HAL or the Kernel.

---

### Post by inci on 2008-05-29
Not quite. HAL is one of the bits of software that handles this (together with libgphoto2, mostly, if I have that right). It seems to me that libgphoto2 actually lacks support for this camera (I've got one myself) but for some reason still tries to mount it as a camera. I'm trying to remove it from libgphoto2, but it's not quite working. I'm planning to get a cardreader tomorrow, but it'd be nice to see this fixed anyway.

I found a bug report for pretty much this issue, claiming it's been fixed - apparently not quite >.>
[https://bugs.launchpad.net/edgy-backports/+bug/175156](https://bugs.launchpad.net/edgy-backports/+bug/175156)

The dirtyfix described in there doesn't actually work for me, for the simple reason that I can't find a rules file for libgphoto2.

Edit: Turning off HAL is one big horrible dirtyfix. So many things are managed by it on a laptop that I'd really prefer not to do that.

---

### Post by jeroenvrp on 2008-05-29
That file is /usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi

Make a backup first (e.g. in your root-dir)

I removed all the lines (between and including 2x [COLOR="Blue"]<match key=[/COLOR] + 2x [COLOR="Blue"]</match>[/COLOR]) where I found DMC- and -LZ and Lumix (just delete instances for all of those cameras to be sure).

After that I restarted hal and udev.

When I plug in the camera now, it is not recognized as a camera, but as a generic usb device.

---

### Post by jeroenvrp on 2008-05-29
So this workaround works. Partly solved.

---


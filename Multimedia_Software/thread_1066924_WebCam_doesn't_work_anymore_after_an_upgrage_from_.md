---
title: "WebCam doesn't work anymore after an upgrage from 8.04 to 8.10"
date: 2009-02-11
forum: Multimedia Software
---

### Post by xela74 on 2009-02-11
Hello,

I have a little problem with my WebCAM a Philips SPC 600NC.
Here the lsusb output:
```

Bus 001 Device 007: ID 0471:0327 Philips WebCam SPC 6000 NC (WebCam w/ mic)

```

With ubuntu 8.04 it used to work perfectly.

When I plug the WebCAM the dmesg output is like below:
```

[ 2151.656077] usb 1-1: new full speed USB device using ohci_hcd and address 5
[ 2151.881293] usb 1-1: configuration #1 chosen from 1 choice
[ 2152.113246] Linux video capture interface: v2.00
[ 2152.129753] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
[ 2152.134268] usb 1-1: SN9C105 PC Camera Controller detected (vid:pid 0x0471:0x0327)
[ 2152.505071] usb 1-1: No supported image sensor detected for this bridge
[ 2152.592670] usbcore: registered new interface driver sn9c102
[ 2152.594289] usbcore: registered new interface driver snd-usb-audio

```

So I tried to compile the latest release of gpsca. The build process has been mage with success but my webcam still doesn't work. I suppose my webcam is still handled by the kernel.

With EasyCAM2 the driver compilation fails.

By the way, the command `uname -r` tells me, my kernel is 2.6.27-9-generic but in the /lib/module folder there is 2.6.27-11-generic folder. So, why the loaded kernel is not the latest one ?

Does someone can help me ?
I've tried a lot of tips using a lot of forum but my webcam is still unusable.

Thanks in advance
Alex.

---

### Post by cariboo on 2009-02-11
According to the output you listed from dmesg there is a driver being loaded.

When you start up Ubuntu does the light on the wecam flash during boot up?

I would suggest you install xawtv, which is in the repositories and type in a terminal:

```
sudo xawtv -c /dev/video0
```

If you can see yourself you webcam is working.

Jim

---

### Post by xela74 on 2009-02-11
When the computer boots up, the webcam's led is turned on and is never turned off.

I forgot to precise that the /dev/video0 file is missing.

I have tried to run xawtv but it doesn't start beacuse of the /dev/video0 which is missing.

the output from xawtv
```

alex@alex-desktop:~$ sudo xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-9-generic)
xinerama 0: 1280x1024+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Aucun fichier ou dossier de ce type
v4l2: open /dev/video0: Aucun fichier ou dossier de ce type
v4l: open /dev/video0: Aucun fichier ou dossier de ce type
no video grabber device available

```

:o(

Thanks for you help

---


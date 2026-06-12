---
title: "Generic Webcam Problems (Cam ID 0c45:602c)"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by teslar on 2006-08-23
Hi,

so I got this cheap camera which is supposed to be supported by the spca5xx driver (ID is 0x0c45 0x602c and that is listed as using the sn9c102 bridge). I want to use it primairly with the Mercury Messenger, which uses JMF and thus apparently V4L1 and that's my problem.

When I first got it, it worked fine out of the box in xawtv, but Mercury Messenger refused to even acknowledge its presence. So, given that it's a sn9c102 camera, the driver for which apparently doesn't do v4l1, I figured I'd try (re)installing the spca5xx driver, following [Arnieboy's instructions](http://ubuntuforums.org/showthread.php?t=75284). That resulted in catastrophic failure, any further attempt to run v4l-conf or xawtv made X lock up.

I then got the [EasyCam2 script](http://forum.ubuntu-fr.org/viewtopic.php?id=16670), which reinstalled the drivers again. This has stopped X from locking up whenever I try v4l-conf, even if I now redo Arnieboy's instructions. So this is a good thing.

The bad thing is, the camera doesn't work anywhere, full stop. Xawtv gives me a black screen, gqcam complains about "Error reading image..." and Camorama says "Could not connect to video device (/dev/video0). Please check connection."

This is the interesting bit from /var/log/syslog when I plug the camera in:
```
Aug 23 20:14:43 localhost kernel: [17215632.172000] Linux video capture interface: v1.00
Aug 23 20:14:44 localhost kernel: [17215632.268000] sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.24a
Aug 23 20:14:44 localhost kernel: [17215632.272000] usb 2-1: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x602C)
Aug 23 20:14:44 localhost kernel: [17215632.332000] usb 2-1: OV7630 image sensor detected
Aug 23 20:14:44 localhost kernel: [17215632.476000] usb 2-1: Initialization succeeded
Aug 23 20:14:44 localhost kernel: [17215632.480000] usb 2-1: V4L2 device registered as /dev/video0
Aug 23 20:14:44 localhost kernel: [17215632.480000] usb 2-1: Optional device control through 'sysfs' interface ready
Aug 23 20:14:44 localhost kernel: [17215632.480000] usbcore: registered new driver sn9c102
Aug 23 20:14:44 localhost kernel: [17215632.540000] usbcore: registered new driver spca5xx
Aug 23 20:14:44 localhost kernel: [17215632.540000] /usr/share/EasyCam2/drivers/spca/drivers/usb/spca5xx.c: spca5xx driver 00.57.10 registered
```

lsusb:
```
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 0c45:602c Microdia Clas Ohlson TWC-30XOP WebCam
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

ls /dev/video*:
```
lrwxrwxrwx 1 root root      6 2006-08-23 20:14 /dev/video -> video0
crw-rw---- 1 root video 81, 0 2006-08-23 20:14 /dev/video0
```

and v4l-conf, if that's of any help:
```
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1280x800, depth=24, bpp=32, bpl=5120, base=0xa8000000
/dev/video0 [v4l2]: no overlay support
```

So, ideally, I'd like to get it working with v4l1 so I can use it with the Mercury Messenger, but I'd be happy enough if someone had any idea why it stopped working in xawtv. Any help would be greatly appreciated :)

cheers,
tes

---

### Post by grenier on 2007-12-19
Hi, I don't know if you still have the webcam, or if you solved your problem but if you do and you didn't...

The problem comes from the sn9c102 module, it isn't the right one (gspca is). You need to:
- blacklist sn9c102 (in the /etc/modprobe.d/blacklist file)
- install the gspca module (through synaptic. I don't use Ubuntu so I don't know the exact name of that package)
- Reboot

And it ought to work (at least it did for me).

---


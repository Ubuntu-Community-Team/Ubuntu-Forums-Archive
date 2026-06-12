---
title: "qcset: ioctl VIDIOCGCHAN (Invalid argument) on karmic + Logitech QuickCam Express"
date: 2009-11-02
forum: Multimedia Software
---

### Post by Tee.Gee on 2009-11-02
Hi,

I was happily running a Logitech QuickCam Express (usb) for months on hardy. I use the 'webcam' package to grab an image every second.
After the upgrade to karmic, the auto exposure detection didn't work anymore. Trying to figure out the problem, I ran qcset -i, which also worked on hardy. Now, all I'm getting is this:
```
qcset: ioctl VIDIOCGCHAN (Invalid argument)
```
So I searched around a bit and found that I might have to build my own qcset and possibly the kernel driver, which I did. I tried both, the qc-usb-source package and sourceforge's qc-usb-0.6.6.tar.gz tuned with 2 patches I found on [launchpad ]("https://bugs.launchpad.net/ubuntu/+source/qc-usb/+bug/213114")to iron out some build errors. I got the kernel module compiled and loaded but qcset still doesn't output anything else than the above error. The sourceforge tarball came with a 'testquickcam' binary, which is supposed to be able to grab a frame from the cam. It's able to get some info from the cam, but grabbing a frame fails in read() mode and results in a segfault via mmap().
I'm assuming, the 'webcam' program uses the same interface to the hardware as qcset and consequently cannot read or set any parameter.
Any suggestions how to fix this?

Here's some output:
```
# lsusb
Bus 001 Device 002: ID 046d:0840 Logitech, Inc. QuickCam Express
# lsmod | grep cam
quickcam               68032  0
videodev               36736  3 quickcam,gspca_main
```

Cheers,
  Tom

---


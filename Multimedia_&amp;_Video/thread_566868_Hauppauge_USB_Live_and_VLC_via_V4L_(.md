---
title: "Hauppauge USB Live and VLC via V4L ("
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by Fordiman on 2007-10-04
Hey.

I bought a server from System76 with intent to use it to pull video from four Hauppage USB Live (bt878) dongles.

I've installed (and even tried recompiling) VLC, modprobed the bttv driver, hunted around synaptic and these forums like a fiend for anything that would help, and I still can't capture video.

Test is using VLC's network stream option, pointing to /dev/video0, no audio.  Error output below:
```
{00000252} v4l demuxer error: cannot get capabilities (Invalid argument)
{00000252} v4l demuxer error: cannot open audio device (No such file or directory)
{00000250} main input error: no suitable access module for `v4l://'
```

dmesg line generated at run of vlc v4l://:
```
{21891.585097} saa7115 0-0025: saa7113 found (1f7113d0e100000) @ 0x4a (usbvision #1)
```

lsusb line for card:
```
Bus 002 Device 002: ID 0573:2d01 Zoran Co. Personal Media Division (Nogatech) Hauppauge USB-Live Model 600
```

Relevant lsmod lines:
```
bttv                  174260  0
video_buf              26116  1 bttv
ir_common              31236  1 bttv
compat_ioctl32          2304  1 bttv
i2c_algo_bit            8712  1 bttv
btcx_risc               6024  1 bttv
tveeprom               15888  1 bttv
usbvision              75308  0
videodev               28032  2 bttv,usbvision
v4l2_common            25216  4 bttv,saa7115,usbvision,videodev
i2c_core               22656  5 bttv,i2c_algo_bit,tveeprom,saa7115,usbvision
usbcore               134536  6 xpad,usbvision,usbhid,ehci_hcd,uhci_hcd
```

uname -a
```
Linux ubuntu 2.6.20-16-server #2 SMP Sun Sep 23 19:57:25 UTC 2007 i686 GNU/Linux
```

I have to be missing something.  Perhaps some obscure usbvision or bttv modprobe flag?  Please help!

---

### Post by jeremybear on 2008-01-16
I got this device working (after a fashion) in Gutsy 7.10 by following these steps; prefixed with "sudo" where necessary:

1. Unplug the Hauppauge "USB Live" from the USB port.
2. modprobe bttv
3. modprobe usbvision
4. Plug the "USB Live" back in again
5. dmesg (to check that the device is recognized correctly)
6. apt-get install xawtv motv
7. xawtv -nodga  

If this works, you can try the command "motv" - this launches xawtv with the correct options.

For some reason, it does not work with VLC or TVtime.  The latter thinks the device is a low-res webcam and refuses to open it.  The results you get with xawtv are certainly low-res, but watchable.

---


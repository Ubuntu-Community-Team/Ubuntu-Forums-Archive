---
title: "Logitech Quickcam Pro 5000 &amp; uvcvideo"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by foxjwill on 2006-08-18
Here's what I've done:
```
svn co http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/
make
sudo make install
```

Here's the outcome of make:
```
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
```

Here's the outcome of sudo make install:
```
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  INSTALL /home/avi/checkout/linux-uvc/linux-uvc/trunk/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
depmod -ae
```

Here's the outcome of dmesg:
```
[17179598.860000] Linux video capture interface: v1.00
[17179598.980000] usbcore: registered new driver snd-usb-audio
[17179598.980000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c5)
[17179599.000000] usbcore: registered new driver uvcvideo
[17179599.000000] USB Video Class driver (v0.1.0)

```

Also, when I configured ekiga, it had me use V4L. Is that right?

---

### Post by HumanAnarchist on 2006-08-27
I think uvcvideo uses V4L2 and not V4L. I've got the same webcam and I've also made it work in ekiga, but not in amsn :(

---

### Post by kingrayray on 2006-09-02
I think the current Makefile and whatnot in uvcvideo's SVN repo is borked, i'm not sure.. here's my output of make;

tehrayray@euclid:~/src/uvcdriver$ make
Building USB Video Class driver...
make[1]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make: *** [uvcvideo] Error 2


and it just dies, AFAIK I've installed all the deps, kernel headers, source, etc.. any ideas?

---


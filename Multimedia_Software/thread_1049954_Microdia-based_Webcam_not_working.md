---
title: "Microdia-based Webcam not working"
date: 2009-01-25
forum: Multimedia Software
---

### Post by Alnico on 2009-01-25
I have an Intex Webcam that uses a Microdia chipset. This is the output when I run lsusb:

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0c45:6128 Microdia 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I have installed: gspcav1-20071224.tar.gz from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) -- Did not work

and tried this [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft). But my webcam does not want to work again.

I have attached the output of ```
$ lsusb -d 0c45:6128 -v
``` and ```
dmesg
``` for reference. Desperate to configure my webcam.

---


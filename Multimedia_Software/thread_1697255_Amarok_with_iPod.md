---
title: "Amarok with iPod?"
date: 2011-02-28
forum: Multimedia Software
---

### Post by RobotGymnast on 2011-02-28
I installed a minimal version of Ubuntu, and now Amarok doesn't seem to realize my iPod's plugged in. I have libgpod installed; what am I missing?

Thanks for any help!

---

### Post by johntaylor1887 on 2011-02-28
```
$ mkdir /tmp/packages && cd /tmp/packages

$ wget -nc -c http://archive.ubuntu.com/ubuntu/pool/main/{libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1,libm/libmtp/libmtp-dev_1.0.2-1ubuntu1,libm/libmtp/libmtp8_1.0.2-1ubuntu1,libu/libusb/libusb-0.1-4_0.1.12-14ubuntu0.2,libu/libusb/libusb-dev_0.1.12-14ubuntu0.2}_`dpkg --print-architecture`.deb

$ sudo dpkg --install *.deb

$ sudo apt-get hold libmtp8 libmtp-dev libusb-dev libusb-0.1-4
```
Btw, which version of amarok are you using?

---

### Post by RobotGymnast on 2011-02-28
> **johntaylor1887 said:**
> ```
$ mkdir /tmp/packages && cd /tmp/packages

$ wget -nc -c http://archive.ubuntu.com/ubuntu/pool/main/{libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1,libm/libmtp/libmtp-dev_1.0.2-1ubuntu1,libm/libmtp/libmtp8_1.0.2-1ubuntu1,libu/libusb/libusb-0.1-4_0.1.12-14ubuntu0.2,libu/libusb/libusb-dev_0.1.12-14ubuntu0.2}_`dpkg --print-architecture`.deb

$ sudo dpkg --install *.deb

$ sudo apt-get hold libmtp8 libmtp-dev libusb-dev libusb-0.1-4
```
Btw, which version of amarok are you using?

"Version 2:2.3.2-0ubuntu4" according to Synaptic.
Also, I got "invalid operation hold" for apt-get.

Also, I'm curious as to why you recommended unpacking packages "manually", rather than installing them through apt-get?

Either way, it worked great. Thanks!

---

### Post by johntaylor1887 on 2011-02-28
> **RobotGymnast said:**
> 
Also, I'm curious as to why you recommended unpacking packages "manually", rather than installing them through apt-get?

Either way, it worked great. Thanks!
I just copied what I found at help.ubuntu.com

Glad it worked for ya!

---


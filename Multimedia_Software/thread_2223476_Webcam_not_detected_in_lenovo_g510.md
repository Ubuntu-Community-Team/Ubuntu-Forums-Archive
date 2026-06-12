---
title: "Webcam not detected in lenovo g510"
date: 2014-05-11
forum: Multimedia Software
---

### Post by stanek.94 on 2014-05-11
I have lenvo g510. Cheese and guvcview don't detect my webcam.
Its my lsubs:


```
    Bus 002 Device 002: ID 8087:8000 Intel Corp. 
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 002: ID 8087:8008 Intel Corp. 
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 003 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

How to fix it?

---

### Post by The Bright Side on 2014-05-11
Hey Stanek.94,

Unfortunately, I don't have a solution for you... But I do have the same problem. My PC is the Asus X93S  laptop, and the webcam worked fine on Ubuntu 13.10. I followed the advice [here]("http://community.linuxmint.com/tutorial/view/219"), but to no avail. When I install and run v4l2ucp, I get an error message:

> Unable to open file /dev/video0
No such file or directory

Have you had any breakthroughs by now? Which command did you use to get the output you posted above?

Perhaps we can beat this one.

Thanks,
Matt.

---

### Post by stanek.94 on 2014-05-12
I have the same
Its "lsusb"
Try "lsusb -v" for more info

---


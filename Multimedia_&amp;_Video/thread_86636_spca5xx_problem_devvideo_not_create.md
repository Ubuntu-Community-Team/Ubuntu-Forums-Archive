---
title: "spca5xx problem: /dev/video not create"
date: 2005-11-05
forum: Multimedia &amp; Video
---

### Post by lyly on 2005-11-05
Hi

I' ve a problem with a PAC207 based webcam. 

I've installed the drivers as described in this howto:
[http://www.ubuntuforums.org/showthread.php?p=453021](http://www.ubuntuforums.org/showthread.php?p=453021)

When I connect my webcam, the driver is running:
```
$ lsmod |grep spca5xx
spca5xx               646128  0
videodev                9440  1 spca5xx
usbcore               117884  5 spca5xx,usbhid,ehci_hcd,uhci_hcd

```

but /dev/video0 doesn't existe...

I tried 
```
mknod /dev/video0 c 81 0
```
but no...

Any idea?

Thanks

Lynda

---


---
title: "ZTE MF622 Problem"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by VirtualEdgar on 2009-01-25
Hi guys!

I have a problem with the MF622 dongle. My Intrepid Ibex somehow cannot detect it when I plug it in my laptop, but when I reboot - the Auto Mobile Broadband (CDMA) Connection on NM suddenly shows up and it works. Syslog shows this...

```

Jan 25 18:49:46 my-laptop kernel: [  856.668076] usb 2-1: new full speed USB device using ohci_hcd and address 3
Jan 25 18:49:46 my-laptop kernel: [  856.732081] hub 2-0:1.0: unable to enumerate USB device on port 1
Jan 25 18:49:47 my-laptop kernel: [  857.404048] usb 2-1: new full speed USB device using ohci_hcd and address 4
Jan 25 18:49:47 my-laptop kernel: [  857.671639] usb 2-1: configuration #1 chosen from 1 choice
Jan 25 18:49:47 my-laptop kernel: [  857.896174] usbcore: registered new interface driver libusual
Jan 25 18:49:47 my-laptop kernel: [  857.991528] Initializing USB Mass Storage driver...
Jan 25 18:49:47 my-laptop kernel: [  858.007670] usb-storage: device ignored
Jan 25 18:49:47 my-laptop kernel: [  858.008141] usbcore: registered new interface driver usb-storage
Jan 25 18:49:47 my-laptop kernel: [  858.009188] USB Mass Storage support registered.

```

Help! :)

---

### Post by VirtualEdgar on 2009-01-28
Anyone?

---

### Post by ceefour on 2009-02-06
Probably related to this problem: ( Bug #305968 )

[https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/305968](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/305968)

Have you tried reverting to earlier version of hal-info ?

See also [http://ubuntuforums.org/showthread.php?t=1021366](http://ubuntuforums.org/showthread.php?t=1021366)

> **VirtualEdgar said:**
> Hi guys!

I have a problem with the MF622 dongle. My Intrepid Ibex somehow cannot detect it when I plug it in my laptop, but when I reboot - the Auto Mobile Broadband (CDMA) Connection on NM suddenly shows up and it works. Syslog shows this...

```

Jan 25 18:49:46 my-laptop kernel: [  856.668076] usb 2-1: new full speed USB device using ohci_hcd and address 3
Jan 25 18:49:46 my-laptop kernel: [  856.732081] hub 2-0:1.0: unable to enumerate USB device on port 1
Jan 25 18:49:47 my-laptop kernel: [  857.404048] usb 2-1: new full speed USB device using ohci_hcd and address 4
Jan 25 18:49:47 my-laptop kernel: [  857.671639] usb 2-1: configuration #1 chosen from 1 choice
Jan 25 18:49:47 my-laptop kernel: [  857.896174] usbcore: registered new interface driver libusual
Jan 25 18:49:47 my-laptop kernel: [  857.991528] Initializing USB Mass Storage driver...
Jan 25 18:49:47 my-laptop kernel: [  858.007670] usb-storage: device ignored
Jan 25 18:49:47 my-laptop kernel: [  858.008141] usbcore: registered new interface driver usb-storage
Jan 25 18:49:47 my-laptop kernel: [  858.009188] USB Mass Storage support registered.

```

Help! :)

---

### Post by VirtualEdgar on 2009-02-13
Thanks for the reply ceefour.

Still unsuccessful in recognizing MF622 when I'm inside Ubuntu after applying the solution in the link that you gave. Still, it can only be recognized when I plug in the dongle and restart Ubuntu.

By the way, I'm using 2.6.27-11 kernel. I also have been seeing the following errors in the log...

```

Feb 13 23:17:24 xxx-laptop kernel: [  157.349046] hp[8543] general protection ip:b8020a88 sp:bfe268a8 error:0 in ld-2.8.90.so[b800c000+1a000]
Feb 13 23:17:24 xxx-laptop kernel: [  157.528086] beh[8551] general protection ip:b807aa88 sp:bff801e8 error:0 in ld-2.8.90.so[b8066000+1a000]
Feb 13 23:17:25 edgar-laptop kernel: [  157.601595] hpfax[8557] general protection ip:b805ea88 sp:bfa65ca8 error:0 in ld-2.8.90.so[b804a000+1a000]
Feb 13 23:17:25 edgar-laptop kernel: [  157.619284] hal[8558] general protection ip:b7f9da88 sp:bfda3828 error:0 in ld-2.8.90.so[b7f89000+1a000]

```

I don't know if this would help.

Thanks again!

---


---
title: "Samsung Brightside SCH-U380HKAVZW&#8206; - Mass Storage does not work"
date: 2013-06-11
forum: Mobile Technology Discussions (CLOSED)
---

### Post by mrjagdad on 2013-06-11
I have searched the forums all over, tried a number of things, but have not found a solution.

I have a Samsung Brightside phone with a 16GB Micro SD Card.

I'm running Ubuntu 12.04.1 LTS 

When I connect the phone it does say - Connect to the PC... Call disabled

However I do not see the USB Mass Storage device on my system.

When I connect the device I see the folloing in /var/log/kern.log
Jun 11 21:43:53 ourhome kernel: [1171511.344020] usb 5-1: device descriptor read/64, error -71
Jun 11 21:43:53 ourhome kernel: [1171511.568024] usb 5-1: device descriptor read/64, error -71
Jun 11 21:43:53 ourhome kernel: [1171511.784036] usb 5-1: new full-speed USB device number 52 using uhci_hcd
Jun 11 21:43:53 ourhome kernel: [1171511.908021] usb 5-1: device descriptor read/64, error -71
Jun 11 21:43:54 ourhome kernel: [1171512.188017] usb 5-1: device descriptor read/64, error -71
Jun 11 21:43:54 ourhome kernel: [1171512.292036] hub 5-0:1.0: unable to enumerate USB device on port 1

All help will be appreciated.

Thank you,

Mark

---

### Post by 3rdalbum on 2013-06-14
Try a different USB port.

---


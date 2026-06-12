---
title: "Support for Verizon AD3700 by ZTE"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by cu_ on 2010-01-26
I have been using Ubuntu for a while, but never became an expert at it.  :-(

I used to use Verizon USB760 and this thread ([http://ubuntuforums.org/showthread.php?p=8729020#post8729020](http://ubuntuforums.org/showthread.php?p=8729020#post8729020)) helped me out immensely.

But recently they "upgraded" my USB760 to AD3700 which they said has global support.  But using the same trick as in the thread does not work.  Any ideas?

All I know is, the manufacturer is ZTE.

---

### Post by cu_ on 2010-01-29
Here is the output of my lsusb and uname -r.
I am pretty sure the first one (ONDA Corp...) is the one. 

```

~$ uname -r
2.6.31-17-generic
~$ lsusb 
Bus 001 Device 009: ID 19d2:fff2 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 059b:0251 Iomega Corp. Optical
Bus 001 Device 005: ID 4971:ce12  
Bus 001 Device 003: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 003: ID 413c:2010 Dell Computer Corp. 
Bus 003 Device 002: ID 413c:1003 Dell Computer Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
~$ 


```

---

### Post by pdc on 2010-01-29
you are now running two threads; comments sent to the other

---

### Post by cu_ on 2010-03-11
> **pdc said:**
> you are now running two threads; comments sent to the other
It was an afterthought.  I originally posted in the USB 760 thread and realized, I might need a new thread for this model hardware.

---


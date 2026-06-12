---
title: "usb mobile internet not working on HP Envy Spectre XT"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by 7raTEYdCql on 2013-05-06
Hi Guys,

I've been a user of Ubuntu for a while now. And, my internet dongle worked on my previous Aspire One seemlessly distro after distro, without giving me problems.

However, on my new HP Envy Spectre XT, the mobile dongle gets detected as a mass storage device for some reason. Any idea?

lsusb shows the following device ID 12d1:1446 and names it as a Huawei device.

I just feel it awkward that I need to do some usb_modeswitch, since I never used to do this earlier.


Help would be appreciated,
Regards,
Mehrzad

---

### Post by praseodym on 2013-05-06
Yes, 12d1:1446 is the hard disk mode. USB-modeswitch is recommended

---

### Post by 7raTEYdCql on 2013-05-06
Any help? I am trying to use usb_modeswitch and changing 12d1:1446 to 12d1:140c (read this in many places online)

However, what I don't understand is, how can the dongle work on one computer and not on another: when both run the same version of ubuntu.

Is there something else I am doing wrong?

Regards,
Mehrzad

---


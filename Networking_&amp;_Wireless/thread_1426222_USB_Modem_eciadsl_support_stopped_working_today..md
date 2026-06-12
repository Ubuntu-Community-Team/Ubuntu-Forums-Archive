---
title: "USB Modem eciadsl support stopped working today."
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by Lifman on 2010-03-10
hi, everyone,
after yesterday's routine ubuntu update - allowing both security and recommended updates - i turned off my pc. turning it on today, it seems like my USB modem support is gone. i am using the "eciadsl-usermode_0.12-1_i386" package, and i get the message "/proc/bus/usb/devices: No such file or directory".
i tried re-installing my eciadsl package, but got the same result.
any ideas?

---

### Post by Lifman on 2010-03-10
update:
selecting version 2.6.31-19 (instead of current one, 2.6.31-20) allowed me to use eciadsl-start. is there a way to enable it on 2.6.31-20 also?

---

### Post by Lifman on 2010-03-12
another update:
it seems like the most important error i get is
FATAL: module usbcore not found

how can i fix this?

---


---
title: "Have wireless working and still complain ...."
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by nhanquy on 2009-08-24
I have a Dell Latitude E5500 laptop just installed with Ubuntu 9.04.

1) Looks like it uses Broadcom chip and has** wl** driver for wireless; it attaches **eth3 **as the wireless net interface which is kind of strange to me. 

2) I put the machine running overnight and the next day no network connection; and I had to reboot....Is this Ubuntu or Broadcom driver's problem?



:confused:

---

### Post by shanix on 2009-08-24
Can you paste the result of your:

lspci -vvnn

AND

/var/log/syslog

to pastebin for us to look at?

---

### Post by Iowan on 2009-08-24
> **nhanquy said:**
> 2) I put the machine running overnight and the next day no network connection; and I had to reboot....Is this Ubuntu or Broadcom driver's problem? Some machines seem to have problems with suspend or hibernate. Check your power management settings to see what your machine does after a period of inactivity.

---


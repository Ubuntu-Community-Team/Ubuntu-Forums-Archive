---
title: "Annoying &quot;IOCTL::unknown IOCTL's cmd = ...&quot; message"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by petru.marginean on 2009-11-03
I'm getting this message every 15 seconds in the /var/log/messages.
The wireless works fine.

Any idea how to fix this?

```
$> lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
2.6.31-14-generic

$> lsmod | grep sta
rt2860sta             522456  1 

```Regards,
Petru

---

### Post by petru.marginean on 2012-07-17
Upgrading to the 12.04 version solved the issue

---

### Post by wildmanne39 on 2012-07-17
Hi, thanks for sharing, the thread has been closed, please do not post in a thread that has been inactive for a year or more.
Thanks

---


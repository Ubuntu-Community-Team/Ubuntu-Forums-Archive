---
title: "ping unreachable timings"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by JohnPinto on 2009-11-24
Hi,

when i ping for any ip adress say 192.168.1.59 if the host is reachable it pings for every 1 second. if the device/host(192.168.1.59) stops functioning ...it should give "destination host unreachable" .....(it gives) but i want it to be displayed immediately as soon as the connection to the host is lost..
The ping results are not displayed for about 80 to 90 pings (depends) and after that for once in 3 seconds it says "destination host unreachable".......i want the message to be displayed immediately.

How to do this ?
any settings in any file or anything ?

Thanks
-john;)

---

### Post by lloyd_b on 2009-11-24
> **JohnPinto said:**
> Hi,

when i ping for any ip adress say 192.168.1.59 if the host is reachable it pings for every 1 second. if the device/host(192.168.1.59) stops functioning ...it should give "destination host unreachable" .....(it gives) but i want it to be displayed immediately as soon as the connection to the host is lost..
The ping results are not displayed for about 80 to 90 pings (depends) and after that for once in 3 seconds it says "destination host unreachable".......i want the message to be displayed immediately.

How to do this ?
any settings in any file or anything ?

Thanks
-john;)
You can use the "-W" option to shorten the timeout.```
ping -W 1 192.168.0.200
```Note: "man ping" in a terminal window for a list of all of ping's options.

Lloyd B.

---

### Post by JohnPinto on 2009-11-25
No doesn't work...its same..

---


---
title: "Network manager in Lucid and mobile broadband Huawei"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by axelsvag on 2010-05-02
I have realized that my mobile broad behave differently all of a sudden. I do not know if it have something to do with me updating to Lucid or after an update to the modem I made to get the full 6Mbps.
The problem is this. If I have my mobile broadband modem (huawei220) attached during the boot sequence everything works good. If I detach the modem and attach it again network manager finds it again. But if the modem looses contact, network manager does not automatically connect when the signal is there again as it used to. So I have to manually connect trough network manager. But now comes the real problem. If I do not boot with the modem attached it is impossible to connect with network manager. It just do not find it. Though nautilus find the device and if I use lsusb I can see the modem. What can I do it is annoying to reboot all the time.

Now I have made a another clean install and the problem is still there. But when I tested this on an lucid machine that was updated from karmic everything works as it used to. So it must be possible to get lucid to work on a clean install.

---

### Post by jerzyo on 2010-05-03
I have the same problem, see:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/573242](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/573242)

---

### Post by axelsvag on 2010-05-05
OK, could be something with the 64bit version? Since it works on my 32 bit machines

---

### Post by axelsvag on 2010-05-23
Now I changed to the new kernel 2.6.34 and everything is back to normal.

---

### Post by axelsvag on 2010-05-26
...Or maybe not. I think I got a problem after a while, when the speed seems to drop almost to zero. I think this happens after 10 hours on-line. Maybe it is a brain ghost but I get the feeling that something bad is happening whith this kernel.

Edit 100529 Everything seems to work OK the last days

---


---
title: "Cannot use Sierra Compass 888 with 9.10"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by daithi81 on 2009-12-24
As you may know, it is a mobile broadband device. The company website says that it cannot be used on 9.10, and we will have to wait for 10.x. If this is the case, could someone recommend a Linux distro that can use this device?

---

### Post by ^_Pepe_^ on 2010-01-04
Hi.

I have this modem, and I can use it normally with 9.10 and with good results, just out-of-the-box, no driver installed.

But, there's a bug here, reported by me [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502561](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502561), because the modem only connects at 1st attemp. So, if for whatever reason there's a disconnection, it's impossible to reconnect. There's a loop written to syslog.

After restart, you can connect normally.

Other option, is to use 9.04 version. I've tried it with success also.

Regards, 
^_Pepe_^

---


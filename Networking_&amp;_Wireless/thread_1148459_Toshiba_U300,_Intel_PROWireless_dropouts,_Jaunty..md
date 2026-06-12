---
title: "Toshiba U300, Intel PRO/Wireless dropouts, Jaunty."
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by Mkve on 2009-05-04
Hello,

Description:
I am having a drop out problem with my wireless connection. Every now and then my connection will simply "drop out" (though it still says i am connected to my network) and i am unable to access the Internet for a certain amount of time (it varies, sometimes it fixes instantly and sometimes it may take several minutes for me to access the Internet again).

This problem does not occur while logged into Windows.

Laptop/Hardware Specs:

Model: Toshiba U300.
Using Wicd network manager.

lspci -v | less output:
```

04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
        Subsystem: Intel Corporation Device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 2297
        Memory at f0200000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

```

Note. I am a novice Linux user, so just say if i need to post any other information.

Cheers.

---

### Post by pldg on 2009-05-30
This worked for me, and I tried everything before!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200509/comments/72](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200509/comments/72)

I just transferred an 8GB file without a hitch.

---


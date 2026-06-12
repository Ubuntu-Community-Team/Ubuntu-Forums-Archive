---
title: "Ubuntu changes MAC address at reboot"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by mmasroorali on 2011-10-31
Dear All,
Recently I faced a strange problem of machine MAC address being reset to some strange value and though a work-around solved the problem, I would still like to know the cause, because this is really annoying. Problem like this never happened before.

About four days back, I found that after a reboot, machine MAC address changed to aa:00:04:00:0a:04, where the actual address was far from this. This was also frustrating since my service provider authenticates connections based MAC address and you get disconnected from Internet if your MAC address changes.

After some hours of exasperation, the situation got remedied by setting the cloned MAC address (originally empty) in Edit Connections which is the same as the actual one. See the attached image.

Here is my /etc/network/interfaces file
```

auto lo
iface lo inet loopback
```

So, my machine IP is being set in networking-manager. See the second image. However, setting IP address in /etc/network/interfaces did not solve the problem either. I did not try setting hwaddress in this file.

Since the changed MAC remained the same at every reboot, I suspect that this was hard coded somewhere. And I would like to find out where this was/is coming from.

(I noticed another strange event while starting/stopping network in this scenario, [http://ubuntuforums.org/showthread.php?t=1873117](http://ubuntuforums.org/showthread.php?t=1873117), but I am not sure whether these two issues are related.)

Any pointer will be appreciated.

---

### Post by lisati on 2011-11-13
Thread closed, please see [http://ubuntuforums.org/showthread.php?t=1880514](http://ubuntuforums.org/showthread.php?t=1880514)

---


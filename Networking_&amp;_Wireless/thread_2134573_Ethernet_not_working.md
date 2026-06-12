---
title: "Ethernet not working"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by KeiNivky on 2013-04-11
Suddenly my ethernet stopped working in Ubuntu, it still works in Windows however. At some point in the boot screen the system prints "Waiting for network configuration", then after some time "Waiting up to 60 more seconds for network configuration", a bit later it boots. Also there is this entry in dmesg:

```
r8169 0000:04:00.0: eth0: link down
```

r8169 is my nic driver I guess.

Aparently the nic is not even receiving data, because the leds are not blinking. I don't think this is a physical problem, because, as I said, it works in Windows.

---

### Post by heWhoWearsAshes on 2013-04-11
You might wanna check this out in a while

[http://ubuntuforums.org/showthread.php?t=2134321](http://ubuntuforums.org/showthread.php?t=2134321)

He's having the same problem as you.

---


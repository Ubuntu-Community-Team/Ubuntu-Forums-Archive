---
title: "Hostname error after kernel update"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by flamingsole on 2009-06-19
Hello,

I'm running Ubuntu 9.04, and have been since the update was released. I also have a MacBook Pro on my network, and often SSH into the Ubuntu box by using ```
ssh username@hostname.local
``` I also use this hostname to add the printer to the Mac, and login to run SSH commands, etc.

Today, I installed a kernel update. I can still see Ubuntu in the OSX finder and access files and folders there, but I can no longer SSH into the system by using ```
ssh username@hostname.local
```

It gives the error messge:
```
Could not resolve hostname hostname.local: nodename nor servname provided, or not known
```

However, I can ping hostname.local:
```
64 bytes from 192.168.0.4: icmp_seq=0 ttl=64 time=4.194 ms
```

Any thoughts on this? I restarted Avahi and netatalk, and made sure they were both properly installed and updated.

Thanks for any help,
Jon

---

### Post by flamingsole on 2009-06-19
Well. So sorry for this. The first time I rebooted, nothing worked, so I posted the question. But I rebooted a second time, and everything works again. Try that, if a similar issue occurs with this kernel update.

Thanks,
Jon

---


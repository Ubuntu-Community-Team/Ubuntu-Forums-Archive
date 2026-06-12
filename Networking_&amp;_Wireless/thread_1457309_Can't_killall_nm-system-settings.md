---
title: "Can't killall nm-system-settings"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by kuldeepsidhu on 2010-04-18
in my case it says..
```

sidhu@sidhu-desktop:~$ sudo killall nm-system-settings
[sudo] password for sidhu: 
Sorry, try again.
[sudo] password for sidhu: 
nm-system-settings: no process found
sidhu@sidhu-desktop:~$ 

```

why is this error..?

---

### Post by Iowan on 2010-04-18
Moved to it's own thread.

Is **nm-system-settings** a running process? 
My system has */etc/NetworkManager/nm-system-settings.conf*.
 **sudo ps -ef |grep nm** reveals no **nm-system-settings** process.

---


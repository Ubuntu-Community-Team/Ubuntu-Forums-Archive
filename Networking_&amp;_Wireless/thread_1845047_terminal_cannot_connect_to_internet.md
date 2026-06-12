---
title: "terminal cannot connect to internet"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by mdelacerna05 on 2011-09-16
I am using Ubuntu 11.04, and when I try to install programs through the terminal, and they happen to need internet connection, the terminal always says that there is a connection failure; even when I only type apt-get. The same thing happens using the Ubuntu Software Center. I can connect to the internet through my browser though. I already tried doing this as root.

---

### Post by haqking on 2011-09-16
> **mdelacerna05 said:**
> I am using Ubuntu 11.04, and when I try to install programs through the terminal, and they happen to need internet connection, the terminal always says that there is a connection failure; even when I only type apt-get. The same thing happens using the Ubuntu Software Center. I can connect to the internet through my browser though. I already tried doing this as root.


typing just apt-get will only tell you about apt-get and not connect to anything anyway.

Can you ping anything from your terminal ?
```

ping -c 3 google.com
```

It is likely a sources issue

---


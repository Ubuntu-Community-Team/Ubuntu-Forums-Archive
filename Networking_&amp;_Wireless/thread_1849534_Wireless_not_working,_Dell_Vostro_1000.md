---
title: "Wireless not working, Dell Vostro 1000"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by zeii on 2011-09-24
I'm using 11.04 on a Dell Vostro 1000, drivers are installed (BCM4311) but i cannot see it in the network manager... any fixs?

Note: Already tried to add this to /etc/network/interfaces
```
auto wlan0
iface wlan0 inet dhcp
```

---

### Post by mörgæs on 2011-09-25
Have you tried this thread?
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by bkratz on 2011-09-25
> **zeii said:**
> I'm using 11.04 on a Dell Vostro 1000, drivers are installed (BCM4311) but i cannot see it in the network manager... any fixs?

Note: Already tried to add this to /etc/network/interfaces
```
auto wlan0
iface wlan0 inet dhcp
```


here is the "official" fix for the BCM4311

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---


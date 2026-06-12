---
title: "How to share internet connection on Ubuntu Jaunty"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by goxi on 2009-06-30
I have DSL internet conection that goes through broadband router with auto DHCP. I also have USB Prolific network adapter (USB to USB connection) that connects PC with Ubuntu and PC with Puppy Linux. How to share my internet connection (eth0) with USB network adapter (usb0) I tried to bridge them but without result.

---

### Post by jamest09 on 2009-06-30
Make you ubunutu box a router -:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

And set is as the default gateway for the other machine.

---

### Post by superprash2003 on 2009-06-30
you could use firestarter or this [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---


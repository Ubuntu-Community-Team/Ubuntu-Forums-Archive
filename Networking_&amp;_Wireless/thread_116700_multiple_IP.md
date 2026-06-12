---
title: "multiple IP"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by raaguileraa on 2006-01-13
Hi everyone

i have a simple question: does anyone knows how to configure multiples IP in one single network card simultaneous?

I used to do this in SuSE and it was pretty simple, creating a "eth0:0". I tried that on Breezy and it became a complete mess...

P.D. I have DHCP for the first IP

---

### Post by Mr_Grieves on 2006-01-13
Just like in SuSE you may use ifconfig:
[http://www.computerhope.com/unix/uifconfi.htm](http://www.computerhope.com/unix/uifconfi.htm)


For example:
```

sudo ifconfig create eth0:1
sudo ifconfig eth0:1 address 192.168.1.2
sudo ifconfig eth0:1 netmask 255.255.255.0

```

---


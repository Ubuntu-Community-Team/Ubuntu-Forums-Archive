---
title: "Wireless disconnects periodically with Broadcom STA"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by b0rderline99 on 2012-05-01
I am using the wl driver from broadcom with my bcm43225 chipset.  I can connect to wifi and everything seems to work fine, but every 15 minutes or so the wireless will disconnect and take a minute or two to reconnect to the network.

Any idea what is going on?  I was using the same driver with the 12.04 beta and it worked almost flawlessly.  The problem only started when I reinstalled the final release.

Thanks!

---

### Post by brainwash on 2012-05-01
Did you check any log files like dmesg? Maybe there are some entries which might help to solve the mystery:
```
dmesg
```

---

### Post by b0rderline99 on 2012-05-02
all that seems to pop up when it disconnects is the following
```
[33215.280149] eth1: no IPv6 routers present
```

It is probably also worth noting that I have IPv6 turned off

---

### Post by b0rderline99 on 2012-05-03
Anyone else having this problem?  This is really annoying!

---


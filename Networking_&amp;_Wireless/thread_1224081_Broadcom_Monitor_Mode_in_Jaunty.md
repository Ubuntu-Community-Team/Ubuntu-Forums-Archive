---
title: "Broadcom Monitor Mode in Jaunty"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by wareagle on 2009-07-27
In hardy and intrepid, I was able to make a virtual network interface by typing

```
sudo iw dev wmaster0 interface add mon0 type monitor
```

When I try to do this in Jaunty, I get the message:
```
command failed: NO such device (-19)
mon0: ERROR while getting interface flags: No such device
```

Any idea what changed?

---

### Post by wareagle on 2009-08-02
I am able to get it to work by installing aircrack-ng and typing
```
sudo airmon-ng start wlan0
```

:D

---


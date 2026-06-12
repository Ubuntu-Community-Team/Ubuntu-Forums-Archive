---
title: "usb-serial port"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by reica on 2012-04-29
Ubuntu 12.04 seems to have a problem with /dev/ttyUSB0
I have 10.04 and 12.04 running on the same computer (Dell Inspiron 560)
In 10.04 the port works perfectly. In 12.04 the port /dev/ttyUSB0 is installed (prolific 2303) but can't be opened.
Anyone with similar problem? Any solutions?

---

### Post by alexfish on 2012-04-29
wondering if this a permissions problem

can check with
```
ls -al /dev/ttyUSB0
```

to give user permissions try as root

```
sudo chmod 666 /dev/ttyUSB0
```or
```
sudo su
chmod 666 /dev/ttyUSB0
```then check with "ls -al /dev/ttyUSB0"

---

### Post by reica on 2012-04-29
Nail on the head! Permission problem. Everything working fine now. Thanks

---


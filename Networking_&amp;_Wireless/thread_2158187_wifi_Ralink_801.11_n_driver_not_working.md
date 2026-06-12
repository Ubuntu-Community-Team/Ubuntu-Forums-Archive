---
title: "wifi Ralink 801.11 n driver not working"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by shahan on 2013-06-28
I have installed ubuntu 10.04.2 on my HP mini
Due to low frequency of the wifi, I had to connect an external device to access wifi internet on it.(only a specific wifi connection)
I have black list the ralink by
```

sudo gedit /etc/modprobe.d/blacklist.conf
```

adding the line
```
blacklist rt2800usb
```
but now I dont find any networks using the external one. what can I do now to use the external one working on my HP mini?
N.B. It works fine on Win7.(32bit)
mine is UBUNTU 10.04.2 (32bit)

---

### Post by ajgreeny on 2013-06-28
Why did you install Ubuntu 10.04.2?

It is no longer supported so any updates to that last iso will need to use the end-of-life repos, but there will be no further security updates after that.

If you really did want 10.04, there was a Ubuntu 10.04.4 version just before it disappeared, but really you should be thinking of an upgrade to a newer version.  If Unity will not run on that netbook try Xubuntu or Lubuntu instead.

---


---
title: "wireless does not work anymore"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by Prisma on 2011-07-03
I updated my system yesterday (Ubuntu 10.10). Few minutes later there was a notification that said something about a program that stop working. Since then I cant connect to the internet anymore. I can see all the wireless networks around me but when I attempt to connect to my home network it keeps asking me for the password.  Anyone experiencing this same issue? i didn't install anything before or after the updates. I am sure there was something on the updates that screwed my system. :confused:

---

### Post by poolet on 2011-07-03
paste the following output here::

```

$ lspci
$ lsusb

```

```
$ lspci -nn | grep 'Wireless Brand'
```
```
$ lsmod | grep 'wlan_mod_name'
```

```
$ dmesg
```

```
$ sudo lshw -C network 
```

---


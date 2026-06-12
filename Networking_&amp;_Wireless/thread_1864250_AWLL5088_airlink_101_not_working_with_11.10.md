---
title: "AWLL5088 airlink 101 not working with 11.10"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by nbrebol on 2011-10-18
i upgraded to oneiric 11.10 and set about installing the modules for my AWLL5088 airlink 101 usb adapter. this consists of getting to the driver directory i downloaded and extracted (rtl8192_8188CU_linux_v3.0.2164.201107150, then running the command
```
sudo insmod 8192cu.ko

```

in ubuntu 11.04 this resulted in the wireless usb springing to life and me happily surfing the internet.

now, all i get is the error message: ```
insmod: error inserting '8192cu.ko': -1 Invalid module format
```

thanks in advance, i know there are already lot of people out there with problems with 11.10 so i am extra appreciative of anyone's help with me on this

---

### Post by praseodym on 2011-10-18
This module cannot yet be build with kernel 3.x.

Try a mainline kernel according to this thread:

[http://ubuntuforums.org/showthread.php?t=1861463&page=4](http://ubuntuforums.org/showthread.php?t=1861463&page=4)

#32

---

### Post by praseodym on 2011-10-18
Double posting

---


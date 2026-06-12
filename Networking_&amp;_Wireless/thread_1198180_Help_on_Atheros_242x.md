---
title: "Help on Atheros 242x"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by pogztimz on 2009-06-27
i'm trying to follow this guide [http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu]("http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu") to make my laptop connect to wireless networks. my card is Atheros AR242x and i'm using jaunty on my laptop.

when i typed ```
make
``` the resulting output on my terminal is this
```
sysadmin@sysadmin:~/madwifi$ cd madwifi-hal-0.10.5.6
sysadmin@sysadmin:~/madwifi/madwifi-hal-0.10.5.6$ make
cd: 1: can't cd to /lib/modules/2.6.28-11-generic/build
Makefile.inc:66: *** /lib/modules/2.6.28-11-generic/build is missing, please set KERNELPATH.  Stop.
sysadmin@sysadmin:~/madwifi/madwifi-hal-0.10.5.6$
```

any help?

---

### Post by pogztimz on 2009-06-27
ANSWER: 

```
sudo apt-get install linux-headers-$(uname -r)
```

---


---
title: "Network-Manager and DHCLIENT FAIL, Natty"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by afrodeity on 2011-05-29
I've removed and reinstalled network-manager several times. After the natty upgrade, I managed to resolve my network problem by reinstalling network-manager, but now the problem is back again.

The only way I can get online is to run sudo pppoeconf.

I have to do this every time I reboot.

pon dsl-provider fails

sudo dhclient fails

I have already changed network conf settings to managed=yes

There might be a permissions or ownership problem with dhclient script, but dhclient directory leases are all owned by root:root

Any ideas?

---

### Post by afrodeity on 2011-05-29
These are the permissions on dhclient-script
```

-rwsr-xr-x  1 root root     8595 2011-04-19 16:56 dhclient-script

```

I've changed them to 777

```

-rwxr-xr-x  1 root root   506544 2011-04-19 16:57 dhclient

```

---

### Post by afrodeity on 2011-05-29
installed versin of network-manager

0.8.4~git.20110319t175609.d14809b-0ubuntu3 (natty)

mainted by ubuntu core developers.

---

### Post by afrodeity on 2011-06-05
Deleting configuration file for Network-Manager works [http://ubuntuforums.org/showpost.php?p=10736509&postcount=2](http://ubuntuforums.org/showpost.php?p=10736509&postcount=2)

Problem partially solved. dhclient solution anybody?

---


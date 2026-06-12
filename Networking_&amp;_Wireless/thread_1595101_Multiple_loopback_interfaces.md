---
title: "Multiple loopback interfaces"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by Sepiraph on 2010-10-12
I searched the forum and found 2 threads, none of which has a satisfactory as to how to add multiple loopback interface from startup:

[http://ubuntuforums.org/showthread.php?t=1455881](http://ubuntuforums.org/showthread.php?t=1455881)

[http://ubuntuforums.org/showthread.php?t=1397372&highlight=multiple+loopback](http://ubuntuforums.org/showthread.php?t=1397372&highlight=multiple+loopback)

For example, if I have in my /etc/network/interface: 

```

auto lo lo:1
iface lo inet loopback

iface lo:1 inet static
address 1.1.1.1
netmask 255.255.255.0
network 1.1.1.0

```

I would still need to go to the command line and execute ```
ifup lo:1
``` I supposed I can use another start-up script to run "ifup lo:1" but couldn't I put all the needed commands in /etc/network/interface?

---


---
title: "default route not set at boot time"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by uboot66 on 2011-11-25
Hi,

just in case that anybody else run into the same problem I had this morning.
I set up a brand new virtual machine with Ubuntu 10.04 and I was wondering why the hell this machine did not come up with a default route when having this content in /etc/network/interfaces:

```
auto eth0
iface eth0 inet static
        address 10.32.0.45
        netmask 255.255.224
        gateway 10.32.1.254

```After poking around I only found an old entry from 2006 in these forums:

[http://ubuntuforums.org/showthread.php?t=164764](http://ubuntuforums.org/showthread.php?t=164764)

Well, this guy had the same problem as I had: the netmask was invalid (in my example the last octet is missing) and therefore the rest of /etc/network/interfaces was ignored. In the example from 2006 I think the netmask line was

```

        netmask 225.225.0.0

```and should look like this:

```

        netmask 255.255.0.0

```After changing the netmask line to a valid netmask the system is running fine.

---


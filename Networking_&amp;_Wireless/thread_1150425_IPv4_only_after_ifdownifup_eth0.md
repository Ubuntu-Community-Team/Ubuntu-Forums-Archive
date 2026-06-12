---
title: "IPv4 only after ifdown/ifup eth0"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by Oakenshields on 2009-05-06
Hello,
recently I detached a Jaunty-Box from NIS that is: uninstalled the NIS client, removed the yp related entries and made a copy of the passwd, shadow and group from the primary server. So far so good- login works. But after reboot I got the following (strange) behaviour:

The Network interface eth0 is (trying) to come up as IPv6 and not as IPv4 as configured in /etc/network/interfaces. Only after doing a
```

# ifdown eth0
SIOCDELRT: No such process
# ifup eth0
 * Starting portmap daemon...
 * Already running.
    ... done
 * Starting NFS common utilities
    ... done

```IPv4 and SSH Login is working.

What also puzzles me is that Iam logged in as [EMAIL="myaccount@localhost.locald"]myaccount@localhost.locald[/EMAIL]omain and not myaccount@myhostname (as I used to). Also the localhost line in the /etc/hosts is rewritten after reboot to
```
127.0.0.1 localhost.localdomain localhost
```Does this sound familiar to someone? I know- never change a running system ;-)...

/etc/hostname
```

myhostname

```/etc/network/interfaces
```

iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 1.2.3.4
        netmask 255.255.255.224
        gateway 1.2.3.5
        auto eth0

```Pete

---


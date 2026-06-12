---
title: "Virtual Network Interface Oddity"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by ducksoup on 2009-05-15
Hello,  I have the following in my /etc/network/interfaces file: -

```
auto eth0
iface eth0 inet static
    address 192.168.2.1
    network 192.168.2.0
    netmask 255.255.255.0
    broadcast 192.168.2.255
    gateway 192.168.2.254

auto eth0:1
iface eth0:1 inet static
    address 192.168.2.50
    network 192.168.2.0
    netmask 255.255.255.0
```If I execute the command /etc/init.d/networking restart, both interfaces come up appropriately.  However, if I reboot the system with this configuration, the startup process hangs when it gets to 'Configuring Network Interfaces'.

If I comment out the eth0:1 section, boot up proceeds as normal with eth0 receiving it's intended configuration.  At this point I can edit the interfaces file, uncomment the eth0:1, restart networking and both interfaces work properly.

What's going on?  Why will this configuration work post boot but not during boot?

Thanks for any help people might have!

---

### Post by ducksoup on 2009-05-16
Anybody?  I still have the problem.  Am running Ubuntu Server 9.04.

Thanks again!

---

### Post by rwilson04 on 2009-05-28
I have the same server, sort of the same problem. Mine doesn't hang, but the virtual interface does not start until I run /etc/init.d/networking restart manually. I might try adding a line to some startup process to execute the networking restart, but I would prefer to do it another way.

---

### Post by S-fish75 on 2009-06-19
Has there been a fix for this issue as I am still getting the problem, virtual interface not starting on boot, need manual start.

again using 9.04 server.

---


---
title: "Default route lost after reboot"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by dokaspar on 2009-09-08
Hi,

I have successfully set up a machine with a static IP address and the following /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
   address xxx.xxx.xxx.xxx
   netmask 255.255.255.0
   gateway 192.168.100.1
```

After rebooting, I always have to manually add a default route to make everything work again:

```
sudo ip route add default via eth0
```

After this, everything is back to normal. What's going on here? 
Why isn't the default route added automatically on reboot?

Best regards,
Dominik

---

### Post by dokaspar on 2010-03-15
I figured out the problem now.
The netmask was set incorrectly.

Dominik

---


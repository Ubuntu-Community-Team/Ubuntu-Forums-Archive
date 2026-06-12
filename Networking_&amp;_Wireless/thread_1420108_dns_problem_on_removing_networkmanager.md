---
title: "dns problem on removing networkmanager"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by u_kapaley256 on 2010-03-02
Hi,

I am using kubuntu 9.10 64-bit on AMD M500 machine
i removed networkmanager (because i had frequent disconnect) and installed wicd but the /etc/resolv.conf had a comment on top which says that it is to be configured by networkmanager (still)
I put the DNS in there manually and it works 
What to put in there so that it uses DHCP ? 
Maybe its set to be not written by anyone other than networkmanager ??

Thanks

---

### Post by Barriehie on 2010-03-02
You can tell an interface to get it's address via DHCP in /etc/network/interfaces file.

Mine looks like this:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet dhcp
  pre-up iptables-restore < /etc/iptables.using
  post-down iptables-save -c > /etc/iptables.using

```

---

### Post by u_kapaley256 on 2010-03-02
Hi,

I tried copying down the thing you've written for eth0 into wlan0 as well
But the /etc/resolv.conf doesn't get written
Thanks for your reply though.

---

### Post by u_kapaley256 on 2010-03-04
Hi,

Interesting solution !!
The /etc/resolv.conf should be a symbolic link to /etc/resolvconf/run/resolv.conf
Thats all there is to it!!
The resolv.conf was not leading to the actual thing and taking matters in its own hands
Hope this helps everyone stuck with this

---


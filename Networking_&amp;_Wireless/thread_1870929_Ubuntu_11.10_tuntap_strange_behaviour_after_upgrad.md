---
title: "Ubuntu 11.10 tun/tap strange behaviour after upgrade from 11.04"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by cpuchip on 2011-10-28
Hi all!

ok, here's the strange thing. I had a tun/tap interface configured under 11.04 to run some qemu/kvm sessions. Everything worked just fine until the online upgrade to 11.10 happened. After the upgrade the system can boot up and pretend to have no connections (nothing works - browser, mail etc). But the ping to the external IPs work well (google dns, for instance). "can boot up" means that there's another strange thing - sometimes networking is ok after booting the system up (with no changes in the configuration)!

under 11.04 everything worked flawlessly for almost half a year.

here's some tech info. 

my /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

iface eth0 inet manual
 
auto tap0 
iface tap0 inet manual
tunctl_user myuser
 
auto br0
iface br0 inet static
bridge_ports eth0 tap0
bridge_maxwait 0
address 10.72.240.80
netmask 255.255.255.0
broadcast 10.72.240.255
gateway 10.72.240.1
```

my /etc/NetworkManager/NetworkManager.conf file:

```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
```

host is connected to the internal network via wired connection (physically on eth0), there's a hw dhcp server in the network. the system is x86-64 desktop.

tried to get rid of the problem, and the approx. workaround that usually helps is as follows:

1. edit the /etc/interfaces and add "auto eth0" string.
2. run deprecated /etc/init.d/networking restart command. as a result eth0 gains IP from dhcp server, and even ping to external IPs stops working. restart network-manager.
3. edit the /etc/interfaces again and remove "auto eth0" string
4. restart networking once again - eth0 looses the IP. restart network-manager - and everything starts working properly.

In other words, the goal is to gain an IP via dhcp on eth0 once, then drop the IP.

As you can imagine, this way of gaining the network access is very annoying one. I'm still not sure if the plan above can help me after any of buggy bootups.

Can anyone suggest the solution? maybe someone have met similar situation before.

Thanks in advance.

---


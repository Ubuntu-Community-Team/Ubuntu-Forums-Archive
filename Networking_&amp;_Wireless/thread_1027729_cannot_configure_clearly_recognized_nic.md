---
title: "cannot configure clearly recognized nic"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by d2e2 on 2009-01-01
I setting up a system to work as a bridge between two networks. After physically enabling the second system card it was assigned an ipv6 address automatically but when I tried to configure it with an ipv4 address the network configuration tool reported that the card does not exist.

This is a new install of Ubuntu 8.04. Everything seemed to work until now. So I do not think there is anything wrong with the install.

This is my first experience with a Debian based system, I have been using Linux(Suse, Red Hat, and Mandivia) for years. So I am not exactly a novice, but the network configuration files on this system are alien to me.

I do not want to go farting around with iproute and/or ifconfig until I understand how all the configuration files work together, so if someone can provide a clue as to why the card is not being recognized, I would be briefly appreciative, eternally being unrealistic for such a small thing.

---

### Post by cariboo on 2009-01-01
In any debian based distribution the network device configuration file is called /etc/network/interfaces. Once you've open the file for editing it is pretty self evident on what needs to be done. Welcome back from the darkside. :)

Jim

---

### Post by mpokrywka on 2009-01-01
Man page doesn't mention bridging configuration, but it is of course available too:
```

iface mybridge inet dhcp
    bridge_ports eth0 eth1
    bridge_fd 0
    bridge_stp off
    bridge_maxwait 0

```
that bridge_fd/bridge_stp/bridge_maxwait are my favourite settings, but only "bridge_ports" is required.
See **zless /usr/share/doc/bridge-utils/README.Debian.gz**

But first make sure you have bridge-tools installed:
```

dpkg -l bridge-tools || aptitude install bridge-tools

```


added: I forgot to mention - you can use **ifdown IFACE; ifup IFACE** to test your changes

---


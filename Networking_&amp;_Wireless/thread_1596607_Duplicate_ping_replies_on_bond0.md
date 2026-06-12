---
title: "Duplicate ping replies on bond0"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by Celauran on 2010-10-14
Hi there,

I have 4 NICs in my 10.04 server, 3 of which I have bonded.  The bond itself is working fine -- I'm able to connect to and from the machine -- but whenever I try to ping out, I get duplicate replies.  Google has, so far, yielded nothing of use.  Anyone encountered this before?

I've included potentially relevant files:

/etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

auto bond0
iface bond0 inet static
    address 10.0.0.2
    netmask 255.255.255.0
    gateway 10.0.0.138
    slaves eth1 eth2 eth3

```

/etc/modprobe.d/bonding.conf
```

alias bond0 bonding
options bonding mode=0 miimon=100

```

---

### Post by relay_man on 2010-10-14
Rather than making an assumption,(you know what happens) I'll ask.

Can you give more detail about how things are connected?

---

### Post by Celauran on 2010-10-15
Setup is:

Modem/Router--Hub--BIX--Hub--Server

---

### Post by Celauran on 2010-12-02
So after having had to put this aside for a time, I'm back looking into it.  It turns out that the method used in bonding ethernet devices [changed in 10.04](https://help.ubuntu.com/community/UbuntuBonding#Ubuntu%2010.04), so I've done the setup over but am still facing the same problem with duplicate ping replies.

Additionally, because things changed in 10.04, most of what I've found on Google is outdated and no longer relevant.  Anyone have any ideas/insight?

Also, now that bond-mode and bond-miimon get set in /etc/network/interfaces, does anyone know if changes to /etc/modprobe.d/bonding.conf are still required?

---


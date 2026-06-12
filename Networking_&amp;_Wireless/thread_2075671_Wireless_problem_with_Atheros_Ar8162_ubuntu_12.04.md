---
title: "Wireless problem with Atheros Ar8162 ubuntu 12.04"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by ksprasad on 2012-10-24
Hi All,

We are finding it difficult to make the wireless work in my friend's laptop. It is a Dell Inspiron. Running on Ubuntu 12.04 with 3.2.0-30-generic kernel.

lspci | grep -i ethernet
```

03:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)

```

Earlier rfkill was showing that the wifi was hard blocked. However wired internet was working fine. So, after few googling we installed the alx driver from compat-wireless-2012-05-10-p.tar.bz2

This is how we did it.
```

tar -xvf compat-wireless-2012-05-10-p
cd compat-wireless-2012-05-10-p
scripts/driver-select alx
make
make install
modprobe alx
```

After the above installation, rfkill all shows:

```

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

But still we are not getting the wireless option.
Is there anything else needs to be done?

iwconfig gives following.
```

ppp0      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

usbpn0    no wireless extensions.

```

Any help will be greatly appreciated. Thanks in advance.

Regards,
ksprasad

---

### Post by ksprasad on 2012-10-24
Anybody having any clue, please..

---


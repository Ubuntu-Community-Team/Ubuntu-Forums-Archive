---
title: "How to change/edit ethernet address (hardware address) mac address"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by aliboy on 2009-03-05
please inform me on how to alter mac address in ubuntu. thanks!

---

### Post by Gagle on 2009-03-05
```

    sudo gedit /etc/network/interfaces

```

And edit it to look like this for example :

```

auto eth0
iface eth0 inet dhcp
       hwaddress ether 01:02:03:04:05:06


```

Hope it helps !

---


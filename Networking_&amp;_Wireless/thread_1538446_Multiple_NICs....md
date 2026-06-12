---
title: "Multiple NICs..."
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by BugBuster on 2010-07-25
Hi I have two ethernet ports as follows;
```

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
03:02.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)

```

I want to manage eth0 i.e. the Realtek one with Network-Manager and eth1, the D-Link one using static ip in /etc/network/interfaces.

When I add a static ip for eth1 in /etc/network/interfaces, Network Manager does not start on boot and hence does not bring up eth0

What shall I do?

---

### Post by Iowan on 2010-07-25
Does eth0 have "Available to all users" checked. Other threads suggest this *should* make it available on boot - rather than waiting for login.

---

### Post by BugBuster on 2010-07-25
> **Iowan said:**
> Does eth0 have "Available to all users" checked. Other threads suggest this *should* make it available on boot - rather than waiting for login.

Thanks Iowan, yes I did have that option checked yet it did not work. What fixed the issue though after a lot of trials is this little change;

Edit '/etc/NetworkManager/nm-system-settings.conf'  and change
```

[ifupdown]
managed=false

```

to
```

[ifupdown]
managed=true

```

---


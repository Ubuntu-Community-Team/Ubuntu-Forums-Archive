---
title: "avahi related question"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by pwaugh on 2010-06-08
I have avahi installed on my Ubuntu laptop, which I allow to obtain an IP from the DHCP server on my LAN WiFi router.

The hostname is "laptop", but if certain conditions are met, the laptop's hostname becomes laptop-2.

```
~$ hostname
latop

~$ hostname -A
laptop-2.local

```

Now, if I were logged into a server on the LAN and wanted to ssh to the laptop, and attempt:

```

~$ ssh laptop.local

```

it will fail (even though it normally works as avahi is also installed).

Now, the main reason I have left the laptop on a dynamic IP is because I do take it with me to other Wifi hotspots and don't want to have to reconfigure it to access the net.

If I "hard code" stuff in /etc/hosts, I'd still need Avahi on the laptop and could still run into this laptop-2 thing (I think).

How would it be best for me to avoid this?

patrick

---

### Post by Iowan on 2010-06-08
I haven't had much luck with **avahi**. If you need a fixed IP address, another option for you would be to have the DHCP server issue a static lease - based on MAC address.

---


---
title: "No DHCPOFFERS received"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by afrodeity on 2011-03-23
Struggling to get an old xubuntu box connected to the net, running 2.6.24-19-generic 

If I try

sudo dhclient eth0

I get 
```

No DHCPOFFERS received
No working leasaes in persistant database -sleeping

```

I have tried rebooting my router to no avail. My other box is connecting fine.

---

### Post by pl@yer on 2011-03-23
Is it setup for DHCP
```

cat /etc/network/interfaces 

```

---

### Post by afrodeity on 2011-03-24
```

auto lo 

iface lo inet loopback

iface eth0 inet dhcp

auto eth0

```

---

### Post by pl@yer on 2011-03-24
I would run wireshark on another system to see if the DHCP request is hitting the wire.

---


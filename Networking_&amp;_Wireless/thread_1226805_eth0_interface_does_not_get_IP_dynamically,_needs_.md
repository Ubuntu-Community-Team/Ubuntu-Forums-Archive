---
title: "eth0 interface does not get IP dynamically, needs to be forced"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by jocampo on 2009-07-29
Hello folks

Network card is recognized by Ubuntu but refuses to take IP dynamically from Internet/Router. Only way I can connect to internet running the following command:

```
dhclient eth0
```

After that, I got an IP and I'm able to browse internet and navigate.

How can I force it to get the IP dynamically every time I reboot or start, without having to run any command?  

I tried adding an entry at /etc/network/interface file 

```
iface eth0 inet dhcp
```

... but no luck, same problem. Any ideas?

Thanks in advance,

---

### Post by jocampo on 2009-07-29
By the way...forgot to mention I'm using Ubuntu Server, with no GUI on it....

---

### Post by jocampo on 2009-07-30
Fixed!

I added the "auto" switch or command on my interface file so now it looks like (see the red line)

```
[COLOR="Red"]auto eth0[/COLOR]
iface eth0 inet dhcp

```

---

### Post by jocampo on 2009-07-30
Fixed!

---


---
title: "MAC Address of Ethernet card"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by abel_bcn on 2009-02-25
Hi.

I need to know the mac address of an ethernet card connected to my desktop (PCI). I think it might be a cause of a problem I'm having with my network manager. Could someone tell me how to or what's the command?

Thnx guys!

---

### Post by smani on 2009-02-25
Look at the output of ifconfig, search for HWaddr.

---

### Post by Demiurgo_linux on 2009-02-25
```
ifconfig | grep HWaddr | awk '{print $5}'
```

I hope that it will help you! ;)

---

### Post by stchman on 2009-02-25
Use:

```
ifconfig -a
```

---

### Post by Demiurgo_linux on 2009-02-25
> **Demiurgo_linux said:**
> ```
ifconfig | grep HWaddr | awk '{print $5}'
```

I hope that it will help you! ;)

One little revision ;)
```
ifconfig | grep [your_device] | awk '{print $5}'
```

Change Your_device with the device's name (eth0, ecc...)

---

### Post by abel_bcn on 2009-02-25
Thanx guys! I completeley forgot about ifconfig.

Still It didn't solve the problem.

Internet works fine, but network manager has a "warning" sign on it, and says that the device is not being managed.

I tried adding the MAC address to the eth0 connection (it was blank), but apparently it didn't fix it.

My /etc/network/interfaces file shows the following, in case it helps:

> auto lo
iface lo inet loopback




iface eth0 inet dhcp



auto eth0

Anyone know what's going on? Btw I'm running Intrepid.

Thanks for any help!

---

### Post by Iowan on 2009-02-25
Network Manager reportedly keeps it's files in a separate place - /etc/NetworkManager (spelling/capitalization may be wrong - I don't have Intrepid to check).

BTW, **sudo lshw -C network** might also reveal MAC address.

---


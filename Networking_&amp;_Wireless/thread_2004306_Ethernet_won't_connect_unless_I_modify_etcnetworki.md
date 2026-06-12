---
title: "Ethernet won't connect unless I modify /etc/network/interfaces"
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by Jolladay on 2012-06-15
Hi there,

I am using a minimal Ubuntu to image mini pc boxes. The script I am using to do this requires network access through ethernet. The problem is, it seems like every new box I get doesn't want to connect to ethernet. Usually I can get it to work by modifying /etc/network/interfaces and adding some variation of

```
auto eth#
iface eth# inet dhcp
```

I'm up as far as eth11. Is there a way to get it to automatically connect to ethernet regardless of what box I am using to boot?

I am plugging in an external HDD with ubuntu on it and booting from that drive.

Thanks so much!

-Jolladay

---

### Post by drdos2006 on 2012-06-15
Sounds like the HDD booting is not finding the Network Interface Cards (NIC). I do not think you need to change the default setting of "eth0" to anything else. DHCP should automatically assign a LAN IP for each machine. I feel something is not correct in the booting procedure.
Is it possible to use a LiveCD to confirm this error happens with HDD and CD ?

Here is my /etc/network/interfaces file:
auto lo
iface lo inet loopback


If you do need to alter /etc/network/interfaces, would you need to add the gateway address of the modem/router ?
e.g.
gateway 192.168.0.1



regards

---

### Post by chili555 on 2012-06-15
> 
Sounds like the HDD booting is not finding the Network Interface Cards (NIC).I think it does. Because it's booting from different machines all the time, udev sets a higher ethX because it sees a different MAC address simply because it's a different underlying computer.

I wonder if you could write some script and drop it into /etc/rc.local to grep ifconfig for the eth number and then simply do dhclient eth<whatever>. I am sure I don't know the definitive answer, but I'd start there

---

### Post by Jolladay on 2012-06-26
Thank you for the input! I ended up using a shell script to wipe out /etc/udev/rules.d/70-persistent-net.rules at each bootup. This way it keeps no record of mac addresses. Seems to be working great!

-Jolladay

---


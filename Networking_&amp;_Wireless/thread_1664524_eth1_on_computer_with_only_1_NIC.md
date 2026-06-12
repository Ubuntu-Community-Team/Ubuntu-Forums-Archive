---
title: "eth1 on computer with only 1 NIC"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by austinium on 2011-01-11
Hi,

I am running Ubuntu10.04 as a Virtual Machine in virtualbox. 

I changed my Networking settings from NAT to Bridged Adapter and manually assigned IP addressing information for eth0 in /etc/network/interfaces. 

For some reason doing /etc/init.d/networking restart didn't bring up the network interface. So i replaced the new /etc/network/interfaces file with the original and rebooted. Now I have eth1 in place of eth0. Under System>Preferences>Network Connections I have Auto Ethernet and eth0. However running ifconfig shows lo and eth1.

How can undo this and get back to having eth0 instead of eth1?

Help!

---

### Post by BbUiDgZ on 2011-01-11
change the interfaces config

```
sudo nano /etc/network/interfaces
```

the restart your networking

---

### Post by sj1410 on 2011-01-11
or to make it back to eth0 you can change it in the file

/etc/udev/rules.d/70-persistent-net.rules

or just delete the file and reboot

---

### Post by austinium on 2011-01-11
the file just has loopback

---

### Post by sj1410 on 2011-01-11
just delete the file and reboot, you'll get back your eth0 from eth1

---

### Post by austinium on 2011-01-11
Thanks this fixed it. any idea why it moved from eth0 to eth1?

> **sj1410 said:**
> or to make it back to eth0 you can change it in the file

/etc/udev/rules.d/70-persistent-net.rules

or just delete the file and reboot

---

### Post by sj1410 on 2011-01-11
its a default behavior. when you changed the network settings the mac address of the network card changed and so a new interface was created.

---

### Post by austinium on 2011-01-11
thanks

---

### Post by beijing5pm on 2011-03-28
> **sj1410 said:**
> its a default behavior. when you changed the network settings the mac address of the network card changed and so a new interface was created.
I have the same problem. And is there any way to change this default behavior? I mean the assignment of the sequence number always start from 0.

---

### Post by sj1410 on 2011-03-29
> **beijing5pm said:**
> I have the same problem. And is there any way to change this default behavior? I mean the assignment of the sequence number always start from 0.

there may be many ways to do that. but what i do is delete the following file on every boot.

```

rm /etc/udev/rules.d/70-persistent-net.rules

```

---


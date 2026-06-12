---
title: "Ubuntu 8.04 NIC's capabilities"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by TheXenophobeist on 2010-06-21
In WindowsXP I am able to assign multiple IP Addresses to a single LAN Card/NIC Port by clicking "Internet connections> Local Area Connection>Internet Protocol (TCP/IP)> Advanced> Add".
 
 
Is there a way to configure an Ubuntu 8.04 LAN connection to use more than one IP address?
 
Thanks

---

### Post by Iowan on 2010-06-21
From Code of Conduct:
> Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.
Your thread was hard to read with that formatting - for me anyway.

---

### Post by cariboo on 2010-06-21
It's pretty simple in Hardy (8.04), open /etc/network/interfaces in a text editor:

```
gksu gedit /etc/network/interfaces
```

And start adding ip addresses. Ith your main interface is eth0 the you would use something like this:

```
# The primary network interface 
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

auto eth0:1
iface eth0:1 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

Once you have finished, restart networking

```
sudo /etc/init.d/networking restart
```


 then use ipconfig to check your ip addresses.

---


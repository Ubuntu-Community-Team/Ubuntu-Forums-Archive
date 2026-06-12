---
title: "Cannot create a new wireless network on Ubuntu 12.04"
date: 2013-08-24
forum: Networking &amp; Wireless
---

### Post by nisargshah on 2013-08-24
Hello,
   I'm not able to create new wireless network on my Ubuntu 12.04 laptop even though I've switched WiFi on. Please help. Here's a [screenshot]("https://docs.google.com/file/d/0B-TyP4sP9s_fVHg4TDR5N2M4b3c/edit?usp=sharing"). When I click on the networking options on top-right corner, the option to create a new wireless connection does not appear. Any help would be appreciated.

Thanks in advance!
Nisarg Shah

---

### Post by steeldriver on 2013-08-24
The 'unmanaged' suggests you've messed with the /etc/network/interfaces file, and network-manager is assuming you want to set up your wireless network there.

If you need help resolving that then post back, including the contents of the file i.e. 

```
cat /etc/network/interfaces
```

---

### Post by nisargshah on 2013-08-24
Yes I did mess with that file once. Here's my interfaces file content -

```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 10.10.0.1
netmask 255.255.255.0

```

---

### Post by steeldriver on 2013-08-24
So comment out those lines

```

auto lo
iface lo inet loopback

# auto wlan0
# iface wlan0 inet static
# address 10.10.0.1
# netmask 255.255.255.0

```

and reboot (or restart the networking and network-manager services). 

FYI if you need to set a static IP you can do so via the network-manager applet (Edit connection --> IPv4 settings --> change method from DHCP to Manual)

---

### Post by nisargshah on 2013-08-24
Thanks a ton! Its working now!

---


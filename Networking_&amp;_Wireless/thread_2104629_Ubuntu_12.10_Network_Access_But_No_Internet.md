---
title: "Ubuntu 12.10 Network Access But No Internet"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by IronLyon on 2013-01-13
Currently I have both Lubuntu 12.10 and Ubuntu 12.10 installed on this computer (I'm trying to remove one but that will be another forum thread) and both are having the same issue. I can connect to my wireless router, but when I try and use either Chromium or Firefox neither will be able to connect to the internet. If you could help that would be great, Thanks!

---

### Post by bronkeydain on 2013-01-14
A few possible causes that come to mind:

1) Maybe you are NOT connected to your network even though it says so. Check if you can ping your router.
```
ping x.x.x.x
```
Where x.x.x.x is the address of your internet router or any other device on your network. Your router would typically be 10.0.0.1 or 192.168.0.1 or 192.168.16.1


2) Maybe your ip settings are not correct? Type commands below and post output here:
```
cat /etc/network/interfaces
```

```
ifconfig
```

3) Do you have a firewall active?
```
sudo iptables -L
```

Try these to start and post output here if you are still stuck...

---


---
title: "List all devices in home network"
date: 2013-06-06
forum: Networking &amp; Wireless
---

### Post by lsusb on 2013-06-06
Is there a command like "lspci" that lists all devices connected to the router without you having to physically check?

I understand you could ping every IP in the address range (subnet) but there must be an easier way. Is there some kind of table that is populated whenever a new device starts sending packets to identify itself?

---

### Post by matt_symes on 2013-06-06
Hi

Personally i use nmap

```
sudo apt-get install nmap
```

```
sudo nmap -sP 192.168.0.0/24
```

..nbtscan..

```
sudo apt-get install ntbscan
```

```
sudo ntbscan 192.168.0.0/24
```

Kind regards

---

### Post by cheeseburger38 on 2013-06-07
Sort of like network discovery? I think such exists in the file browser. Shows only computers though and not stuff like Apple TV

---

### Post by DJWYMAN on 2013-06-07
you could log into your routers interface and it will show you all of the devices connected to it that is what I do when I want to check. the back or bottom of the router should tell you how to do it like for instance mine is [http://www.routerlogin.net/](http://www.routerlogin.net/) and then the login screen pops up.

---


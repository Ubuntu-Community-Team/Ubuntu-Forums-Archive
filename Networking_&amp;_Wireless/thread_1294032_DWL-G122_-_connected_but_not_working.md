---
title: "DWL-G122 - connected but not working"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by froff on 2009-10-17
Hello all
My new DWL-G122 usb hub behaviour is strange.
It normally conntects to router, gets IP from it, says, that is connected, shows signal power but network doesn't work. Switching network interface off/on gives no effect - i connects again and network still doesn't work. Even ping to router by its IP doesn't work :(
To make network interface working I need to unplug the hub and plug it again into usb port. This way works perfectly - every time.
My system: ubuntu 8.10

route command gives:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.128.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
172.16.199.0    *               255.255.255.0   U     0      0        0 vmnet8
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

```

192.168.0.1 is my router.
It's very interesting that this last line appears after 25 seconds after route command call.
Regardless of network interface is working (after "replug") or not (before).

In Windoze hub works ok, so it's not hardware problem.

Anybody can help?

---

### Post by froff on 2009-10-21
ping!

---

### Post by Cuba71 on 2009-10-21
VM conflict ???

---

### Post by froff on 2009-11-05
> **Cuba71 said:**
> VM conflict ???

Probably, but but I can't see any conflict between subnetworks.
So I don't know what to change.

link-local AFAIR has address 169.254.0.0


Problem is definitely connected to vmware. When I start macine on runlevel without vmware network works.

If I run vmware guest when network works it stops to work on host, but works on guest. When I stop guest and kill vmware, network still does not work (but system says - it's connected!)
and replugging usb hub does not help. Only machine restart helps :(


Do You have any ideas what is going on and how to solve?

best regards

---

### Post by froff on 2009-11-05
ping!

please, help!

---


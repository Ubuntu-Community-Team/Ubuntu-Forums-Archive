---
title: "zen kernel need help adding belkin usb wireless g"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by konspiracy on 2011-06-19
hey guys
how and which module do i need to biuld with to get my 
belkin f5d7050
fcc id raxwn4501h
working just like out of the box?
sorry about the bad grammar, i'm just a little frustrated.

---

### Post by chili555 on 2011-06-19
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB)

There are several different versions as you can see. Which one do you have?```
lsusb
```

---

### Post by konspiracy on 2011-06-19
> **chili555 said:**
> [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB)

There are several different versions as you can see. Which one do you have?```
lsusb
```

Bus 001 Device 003: ID 050d:705c Belkin Components F5D7050 Wireless G Adapter v4000 [Zydas ZD1211B]

i did some searching in menu config and didnt find anything.

So how do i get the module to start within the kernel?

---

### Post by chili555 on 2011-06-19
```
$ modinfo zd1211rw | grep 705C
alias:          usb:v[COLOR="Red"]050D[/COLOR]p[COLOR="Red"]705C[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```The module is built in to recent Ubuntu versions. All that should be needed is:```
sudo modprobe zd1211rw
```If it doesn't start on boot, add it to /etc/modules:```
sudo su
echo zd1211rw >> /etc/modules
exit
```

---


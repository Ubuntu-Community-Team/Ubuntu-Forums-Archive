---
title: "Missing eth0"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by Panel on 2012-05-15
Hello

I have installed Ubuntu 12 LTS on hyperv.
After a while my eth0 was missing (ifconfig).

Not sure how to get it back.
I will be grate full for help.

---

### Post by poolet on 2012-05-15
> **Panel said:**
> Hello

I have installed Ubuntu 12 LTS on hyperv.
After a while my eth0 was missing (ifconfig).

Not sure how to get it back.
I will be grate full for help.

open up a new terminal and type:: 

```
sudo ifconfig 
```**then your password**

and paste the output here....
Also did you check your network settings? maybe networking is disable....
if you don't try the following..

```
sudo dhclient eth0
``` (or whatever is your "interface")

---

### Post by Panel on 2012-05-18
Hello

By 'interface' I meant network adapter - eth0

So here is if config result
```

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

As you noticed eth0 is missing (which should be virtual hyperv network adapter), so it would be good point to start.

---

### Post by poolet on 2012-05-18
Try the following::

```
sudo dhclient eth0
```if isn't works 

```
sudo //etc/init.d/network restart
```if the problem still exist.... 

paste the output of the following::: 

```

sudo lshw -C network

``````
uname -mr gt

``````
lspci

``````
lsusb
  
``````
lsmod

```  ```
dmesg

```

---


---
title: "Probly really easy network problem"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by xoron on 2010-10-10
i have installed ubuntu 10.10 through windows via wubi.exe, but it doesnt connect to the network.

its detecting which ethernet port has got a network... when i connect to ethernet port 2, it gives the option to connect to eth1 but it still doesnt "establish a connection"

internet and network works fine on windows 7.

---

### Post by JackNocturne on 2010-10-10
Gives us the output of the following commands in **Terminal**

```
ifconfig
```    &    ```
iwconfig
```

---

### Post by xoron on 2010-10-10
> **JackNocturne said:**
> Gives us the output of the following commands in **Terminal**

```
ifconfig
```    &    ```
iwconfig
```



```
maher@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:9c:d4:de  
          inet6 addr: fe80::21b:fcff:fe9c:d4de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2222 (2.2 KB)
          Interrupt:33 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:9c:e1:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:34 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB)

maher@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.


```

---

### Post by JackNocturne on 2010-10-10
ok , im no linux guru or anything but i try & learn by helping

It seems you have two interfaces (as you said)  , they are both ethernet?

I think the problem is there is a conflict between them. So disable one & enable the other one.

So for instance you want to enable [B]eth0
[/B]```
sudo ifconfig eth0 up
``` & 

and disable the other one
```
sudo ifconfig eth1 down
```or vice-versa

---

### Post by xoron on 2010-10-10
[QUOTE=JackNocturne;9949155]ok , im no linux guru or anything but i try & learn by helping

It seems you have two interfaces (as you said)  , they are both ethernet?

I think the problem is there is a conflict between them. So disable one & enable the other one.

So for instance you want to enable [B]eth0
[/B]```
sudo ifconfig eth0 up
``` & 

and disable the other one
```
sudo ifconfig eth1 down
```


Thanks for trying but that didn't make any difference and vice-versa disabled both. So I undid it but still no network :s

---


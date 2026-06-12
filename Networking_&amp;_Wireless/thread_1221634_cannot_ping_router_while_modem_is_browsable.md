---
title: "cannot ping router while modem is browsable"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by garibaldino on 2009-07-24
Hi

I have added a dsl lan/wlan router to my dsl modem. 

I am having a hard time browsing/pinging the router wizard 192.168.1.1 while i can browse the modem wizard 192.168.1.3 as well surfing the web.

Note that dsl modem use dhcp and the router works on default factory settings.



Here are the details

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:24:8c:3c:1e:3b
          inet addr:192.168.1.4  Bcast:192.168.1.7  Mask:255.255.255.248
          inet6 addr: fe80::224:8cff:fe3c:1e3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17736 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000
          RX bytes:18930779 (18.9 MB)  TX bytes:3333979 (3.3 MB)
          Interrupt:251

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2543 (2.5 KB)  TX bytes:2543 (2.5 KB)

```

netstat -r
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.248 U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.1.3     0.0.0.0         UG        0 0          0 eth0

```

I added a 192.168.1.1 default gateway for the router as the modem as one but cannot ping anyway.

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.248 U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
default         192.168.1.3     0.0.0.0         UG        0 0          0 eth0

```

I have hard-reset my router as well.

any clues?

thanks

---

### Post by superprash2003 on 2009-07-24
you could try disabling the dhcp server of the router and enabling the dhcp in modem and allowing the pcs to get an ip from modem.. that may fix it

---

### Post by garibaldino on 2009-07-24
> **superprash2003 said:**
> you could try disabling the dhcp server of the router and enabling the dhcp in modem and allowing the pcs to get an ip from modem.. that may fix it

thanks for reply

but my problem is reaching the wizard for the router device, i.e. 192.168.1.1.

---

### Post by wojox on 2009-07-24
How do you log into your router 

192.168.1.1

or 

192.168.1.3

---

### Post by garibaldino on 2009-07-24
> **wojox said:**
> How do you log into your router 

192.168.1.1

or 

192.168.1.3

i log to the router with 192.168.1.1 & to the modem with 192.168.1.3

---

### Post by martinbaselier on 2009-07-24
First your modem, is a modem/router. So now you have 2 routers in your network. I hope you disable you dhcp in at least one of them. It's probably easier to connect to your second router, when it's not attached to your modem/router.

What do you want to do exactly with the two routers?

---

### Post by wojox on 2009-07-24
That's really strange that it see's your modem but not your router.

---

### Post by garibaldino on 2009-07-24
> **martinbaselier said:**
> First your modem, is a modem/router. So now you have 2 routers in your network. I hope you disable you dhcp in at least one of them. It's probably easier to connect to your second router, when it's not attached to your modem/router.

What do you want to do exactly with the two routers?

OK thanks 

i had to get into full bridge mode

---


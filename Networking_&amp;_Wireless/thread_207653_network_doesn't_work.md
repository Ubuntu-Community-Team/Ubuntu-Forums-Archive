---
title: "network doesn't work"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by precinto on 2006-07-02
Hello everybody.

I just installed my new shipped Ubuntu into my sister's desktop computer. Everything installed correctly. 

When I first booted it told me there were 96 updates available, so I reckon it reached the internet, but when I try to install them it says the repositories are unreachable. Web doesn't work either, etc.

I went to System/Administration/Net and saw the eth0 (ethernet connection) was deactivated. But it doesn't let me activate it, it just says I should check if it is correctly connected and configured...

I can't ping Google, neither by name nor ip. It says network is unreachable.

I'm using a router. The internet cable is connected to the router and the router is connected to my sister's pc through a network cable. While I use the wifi connection. I've tried to connect directly from the modem to the desktop pc (didn't restart), but it didn't work.

Thanks for all your help.

EDIT: I forgot to say it was a fresh install. I formatted the whole 40gb hd and installed just linux, since windows won't install anymore, who knows why...

EDIT2: I can ping localhost. And this is the ifconfig:
> 
lo     Link encap:Local Loopback
       inet addr:127.0.0.1 Mask: 255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:163436 Metric:1
       RX packets:7 errors:0 dropped:0 overruns:0 frame:0
       TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:372 (372.0 b) TX bytes:372 (372.0 b)


And this is my /etc/network/interfaces:

> 
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


---

### Post by precinto on 2006-07-02
Now I just changed DHCP to Static IP and set it manually and everything is working... Is this a good solution for the long term?

Thanks.

---

### Post by mips on 2006-07-02
I use static addresses but some people prefer dynamic. Solution is fine as long as the routers LAN subnet does not change.

---

### Post by precinto on 2006-07-03
Ok, thanks a lot, mips. : )

---

### Post by sethfc on 2006-07-03
what were the #s you put into static IP?
i tried static IP and this IPv6 deal and i still cant connect to the internet

---

### Post by precinto on 2006-07-03
I used the IP assigned by the router. Since that computer is connected to the router with a network cable I think it will have the same ip most of the time. Tipically IPs from the router, AFAIK, are 192.168.X.X. In my case it was 192.168.2.2, but for you it can it other (try 192.168.0.2/3...).

But may be your case is absolutely different from mine...

Good luck.

---


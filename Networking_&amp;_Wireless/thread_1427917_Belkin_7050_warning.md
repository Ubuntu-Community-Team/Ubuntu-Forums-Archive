---
title: "Belkin 7050 warning"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by NoobieDoobieDo on 2010-03-12
Hi,

For two days I've tried to get my new Belkin 7050 wifi stick up and running.  No matter what I did nothing changed, at all.  After close to 8hrs of straight trouble shooting I have made zero progress.  Zero.

If you have a bunch of free time and want a project then feel free to play with this device.  However if you're short on time or have work to get done just take it back to the store and get a different device.

Here's the over view of my situation : 

- Ubuntu 8.04 : Device is detected.  DHCP = Doesn't connect to router / get IP.  Router can see device.  Router has no security / password enabled.

After several hours of trouble shooting Ubuntu I booted into win2k (supported by device)

- Win2k : Device is detected, official software installed.  DHCP = Doesn't connect to router / get IP.

It does the exact same thing in Win2k as it does in Ubuntu.

- Ubuntu 9.10 : Did a fresh install if 9.10 just to trouble shoot this problem.  Symptoms are exactly the same.  DHCP doesn't get an ip.  There are no errors in /var/log/messages

- Ubuntu 9.10 : Blacklisted the regular drivers and did the ndiswrapper method, smooth sailing.  After all is said and done *_it does the exact same thing_*.  DHCP doesn't get an ip.

In all the trouble shooting I did (iwconfig, ifconfig, etc) I never received any error messages telling me that something had went wrong (besides the part where dhcp didnt get an ip).

on the back of the stick it says : F5D7050B
windows says : its revision 3 of the hardware
linux says the usb id is : u50d:705a
linux identified it as : F5D7050a

long story short : **this device works ok for some people but doesn't work at all for others.  in my situation _no matter what i did nothing changed at all_.**

[157 amazon reviews = 2.5 stars]("http://www.amazon.com/F5D7050-Wireless-802-11g-Network-Adapter/dp/B0002HA7FY")

[72 walmart reviews = 3 stars]("http://www.walmart.com/ip/Belkin-F5D7050-Wireless-G-54Mbps-USB-Network-Adapter/3756936")

[152 newegg reviews = 3 stars]("http://www.newegg.com/product/product.aspx?item=N82E16833314011")

edit : I have another PC connected to the same router.  The router is fine.  The internet connection is fine.

---

### Post by inobe on 2010-03-12
sounds like you have dsl and a wrong nameserver

---

### Post by NoobieDoobieDo on 2010-03-12
not even close.

---

### Post by coffeecat on 2010-03-12
> **NoobieDoobieDo said:**
> on the back of the stick it says : F5D7050B
windows says : its revision 3 of the hardware
linux says the usb id is : u50d:705a
linux identified it as : F5D7050a

I'm posting courtesy of a Belkin USB WiFi stick. It says F5D7050B on the back.

And from lsusb:

```
Bus 002 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
```Seems to be identical to yours. I get a stable connection with it in Jaunty, Karmic and Lucid Apha. Which bears out your statement:

> **NoobieDoobieDo said:**
>  long story short : **this device works ok for some people but doesn't work at all for others.  in my situation _no matter what i did nothing changed at all_.**I'm sorry to hear it.There must be a logical explanation - you seem to have excluded a router issue - so keep at it. Despite your unfortunate experience this is a Linux-friendly device. If I think of anything I'll post again.

Good luck!

---

### Post by NoobieDoobieDo on 2010-03-13
Thanks but im pretty sure this is never going to work.  I mean, i tried it in the support os with the official drivers and the official software and nothing happens.  That can't be a good sign right?

---

